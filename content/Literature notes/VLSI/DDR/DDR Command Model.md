2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #architecture

## Core idea
DDR access is not a single direct "read address X" or "write address Y" action.

A DDR bank usually follows this lifecycle:

ACT -> RD/WR -> PRE

This means:
- **ACT (Activate)** opens a row in a bank
- **RD / WR** accesses columns within the already open row
- **PRE (Precharge)** closes the open row and returns the bank to idle

The bank-level command flow exists because DRAM first opens a full row into the sense amplifiers / row buffer, and only then accesses selected columns from that active row.

---

## Why this command model exists
DRAM cells are small capacitors, so the array cannot be accessed like SRAM.

To read or write:
1. a row is selected and sensed
2. the row becomes active in the row buffer / sense amplifiers
3. columns are selected from that active row
4. the row is later closed so another row can be opened

So the DDR command protocol is really a way of controlling the row buffer.

---

## Main commands

See also: [[DDR Commands]]

### ACT — Activate
ACT selects:
- a bank
- a row

It opens that row and loads it into the sense amplifiers / row buffer.

After ACT, the bank is in **row-open** state.

```text
Before ACT:
Cell array row is closed

After ACT:
Selected row <-> Sense amps / Row buffer
```

Key idea:
**ACT opens a row, not a column.**

See:
* [[ACT opens a row into the row buffer]]

---

### RD — Read

RD selects a column within the currently open row.

Meaning:

* row must already be active
* RD does not open a new row
* data appears after read latency

```text
ACT opens row 100
RD col 20 reads from row 100, column 20 onward (burst)
```

Key idea:
**RD works only on an already open row.**

See:
* [[RD reads columns from an already open row]]

---

### WR — Write

WR selects a column within the currently open row and writes new data there.

Important clarification:
WR is best understood as writing through the **active row-buffer / sense-amp path** into the selected cells of the open row.

So it is not:

* "direct write to closed cells without ACT"

It is closer to:

* controller drives data
* selected open-row columns are updated through the active row-buffer path
* data is restored into the cells of that open row

```text
ACT:
cell array row -> row buffer

WR:
controller data -> selected columns in row buffer path -> cells of open row
```

Key idea:
**WR requires an active row just like RD does.**

See:
* [[WR writes through the active row buffer path]]

---

### PRE — Precharge

PRE closes the currently open row in a bank.

What PRE does:

* disconnects the active row from the sense amps / row buffer
* equalizes / precharges the bitlines back toward their neutral reference state
* returns the bank to idle so another ACT can happen later

What PRE does **not** do:

* does not erase stored data
* does not "reset columns"
* does not clear memory contents

```text
Before PRE:
Open row <-> Row buffer

After PRE:
No row open
Bank idle
Bitlines equalized
```

Key idea:
**PRE resets the bank access state, not the user data.**

See:
* [[PRE closes the row and equalizes the bitlines]]
* [[PRE does not erase column data]]

---

## Full read sequence

Example:

* Bank = 2
* Row = 100
* Column = 20

Command flow:

```text
1. ACT bank=2, row=100
2. wait tRCD
3. RD  bank=2, col=20
4. data appears after CL
5. PRE bank=2
6. wait tRP
```

Timeline:

```text
time --->

ACT ----------- RD ---------------- PRE
    <- tRCD ->     <- data after CL ->
```

Meaning:

* ACT opens the row
* tRCD allows sensing/opening to complete
* RD selects the column in that open row
* data comes after read latency
* PRE closes the row
* tRP prepares the bank for the next ACT

---

## Full write sequence

Example:

* Bank = 2
* Row = 100
* Column = 20

Command flow:

```text
1. ACT bank=2, row=100
2. wait tRCD
3. WR  bank=2, col=20
4. controller drives write burst
5. wait write recovery as needed
6. PRE bank=2
7. wait tRP
```

Timeline:

```text
time --->

ACT ----------- WR ---------------- PRE
    <- tRCD ->     <- write burst ->
```

Important:
After WR, precharge cannot happen immediately; the DRAM needs time to safely complete the writeback into cells. This is why timings like **tWR** exist.

---

## Row hit vs row miss

### Row hit

Requested row is already open in the bank.

Then the controller may issue RD/WR directly.

```text
Open row = row 100
Request: row 100, col 40
-> RD/WR directly
```

### Row miss

Requested row is not the currently open row.

Then the controller must close the old row and open the new one.

```text
Current open row = row 100
Request needs row 220

PRE -> ACT row 220 -> RD/WR
```

Key idea:
**Same row = fast reuse**
**Different row in same bank = close then reopen**

See:
* [[Row hit vs row miss in DDR]]

---

## Auto-precharge

Instead of sending an explicit PRE later, the controller can request auto-precharge with the read/write.

Examples:

* Read with Auto-Precharge
* Write with Auto-Precharge

Conceptually:

```text
ACT -> RDA
ACT -> WRA
```

instead of:

```text
ACT -> RD -> PRE
ACT -> WR -> PRE
```

Usefulness:

* good when row locality is low
* not always best if the same row may be reused soon

Key idea:
**Auto-precharge trades row reuse for simpler closing behavior.**

See:
* [[Auto-precharge trades row reuse for automatic close]]

---

## REFRESH

DRAM cells leak charge, so rows must be periodically refreshed.

REFRESH is:

* a maintenance operation
* required for data retention
* not an ordinary read/write access

Key idea:
**DRAM is dynamic memory, so refresh is mandatory.**

See:
* [[REFRESH is mandatory because DRAM cells leak]]

---

## MRS — Mode Register Set

MRS programs DRAM operating behavior.

Typical things configured include:

* latency-related settings
* burst behavior
* termination / operating modes

Key idea:
**MRS configures behavior; it is not normal data access.**

See:
* [[MRS configures DRAM behavior]]

---

## ZQ calibration (high level)

ZQ calibration tunes output driver / termination impedance for correct signaling.

At this stage, the important point is:

* it is part of setup/calibration
* not part of the normal ACT/RD/WR/PRE data path

---

## Bank interleaving

The command lifecycle is per bank.

That means one bank can be waiting for activation or precharge while another bank is serving data.

```text
Bank 0: ACT ---- wait ---- RD ---- PRE
Bank 1:      ACT ---- wait ---- RD ---- PRE
```

Key idea:
**Individual banks are constrained, but the memory system gains throughput by overlapping work across banks.**

See:
* [[Bank interleaving improves DDR throughput]]

---

## Most important clarifications from my doubts

### Doubt 1: Does WR write directly to the row or to the row buffer?

Best mental model:

* ACT opens the row into the sense amplifiers / row buffer
* WR updates selected columns through that active row-buffer path
* data is then restored into the cells of that open row

So WR does not bypass the open-row mechanism.

### Doubt 2: What exactly does PRE do?

PRE:

* closes the open row
* disconnects row and sense amps
* equalizes bitlines
* returns bank to idle

PRE does **not** erase memory contents.

### Doubt 3: Does PRE reset columns?

No.
Columns are just the selected access positions within the currently open row.
PRE resets the bank's access state, not the stored column data.

---

## Compact mental model

```text
Closed bank
   |
   | ACT
   v
Open row in row buffer
   |
   | RD / WR
   v
Column access + burst transfer
   |
   | PRE or Auto-PRE
   v
Bank idle again
```

---

## Exam-style summary

* ACT opens a row
* RD reads columns from the open row
* WR writes columns into the open row
* PRE closes the row and restores bank idle state
* REFRESH preserves data retention
* MRS configures DRAM behavior
* Auto-precharge closes the row automatically after access
* Row hits are faster than row misses
* Interleaving across banks improves throughput

---
