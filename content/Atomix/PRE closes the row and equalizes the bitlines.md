2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #precharge

## Statement
PRE (Precharge) closes the active row, disconnects the row from the sense amps, equalizes/precharges the bitlines, and returns the bank to an idle state.

## Why it matters
A bank must be closed/precharged before a new row can be activated. It resets the access state so a new request can proceed.

## Mini visual
```text
Before PRE:
Open row <-> Row buffer

After PRE:
No row open
Bank idle
Bitlines equalized
```

## Links

* [[1.4 DDR Command Model]]
* [[PRE does not erase column data]]
* [[ACT opens a row into the row buffer]]
