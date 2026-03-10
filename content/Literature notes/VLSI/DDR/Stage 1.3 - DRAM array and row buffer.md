2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #architecture #row_buffer

## Purpose
This chapter explains how DDR moves from single-cell physics to real bank/row/column access.

Stage 1.3 in the roadmap focuses on:
- rows
- columns
- wordlines
- bitlines
- sense amplifiers
- row buffer
- open row
- what ACT really opens

---

## Big picture

A DRAM device is not accessed as one flat bit array.

```text
Channel
  -> Module / SoDIMM
    -> Rank
      -> Chip
        -> Bank
          -> Row
            -> Column
```

The important Stage 1.3 unit is the bank.

Inside a bank:

* there are many rows
* each row contains many columns
* activation opens one full row, not one bit

See:

* [[DDR - DRAM array hierarchy]]
* [[DDR - ACT opens a row not a bit]]

---

## What ACT really does

ACT is a row-level command.

```text
ACT(bank, row)
```

This means:

* select a bank
* select a row inside that bank
* connect that row to the bitlines
* sense amplifiers detect and amplify the stored values
* the activated row is now held in the row buffer

This matches the command model in the DDR notes: ACT selects bank and row, then DRAM loads that row into the sense amplifiers. 

```text
Closed bank
   |
   | ACT(bank,row)
   v
Open row in sense amps / row buffer
```

See:

* [[DDR - ACT opens a row not a bit]]
* [[DDR - Row buffer and sense amplifiers]]

---

## What the row buffer is

The row buffer is the currently active row held by the sense amplifiers.

It is not a CPU cache.
It is the practical storage location of the open row after ACT.

```text
weak cell data
   -> bitline
   -> sense amplifier
   -> stable active row
```

This is why later RD/WR commands can work only after ACT on a closed bank.

See:

* [[DDR - Row buffer and sense amplifiers]]

---

## Row address vs column address

A decoded memory request is conceptually split into:

```text
Rank / Bank / Row / Column
```

* row address = which row to open
* column address = which location inside the open row to access

```text
ACT uses: bank + row
RD/WR use: column
```

Example:

```text
Rank 0 / Bank 3 / Row 1200 / Column 64
```

Meaning:

* ACT opens row 1200 in bank 3
* RD/WR later access column 64 within that active row

See:

* [[DDR - Row address vs column address]]

---

## Why “only one bit” is wrong

A cell stores one bit, but a DDR access does not mean one bit moves on the interface.

The better view is:

* ACT opens a full row
* RD/WR select a column within the active row
* chip width and rank width determine how many bits move together

So storage granularity and transfer granularity are different ideas.

---

## Row buffer size calculation

The row buffer size is first calculated per chip.

Formula:

```text
row buffer size = number of columns in a row × chip width
```

If one x8 chip has 1K columns in a row:

```text
1024 × 8 bits = 8192 bits = 1 KB
```

Examples:

```text
x4  chip -> 1024 × 4  = 512 B
x8  chip -> 1024 × 8  = 1 KB
x16 chip -> 1024 × 16 = 2 KB
```

```text
x8 chip row

C0      C1      C2      ...      C1023
[8 bits][8 bits][8 bits]...      [8 bits]
```

See:

* [[DDR - Row buffer size calculation]]

---

## Connecting row buffer to rank

A rank is a group of chips selected together as one logical unit. A common DDR4 rank is 64 bits wide. 

Example:

```text
8 x8 chips -> 64-bit rank
```

When ACT is sent to the selected rank:

* every chip in that rank opens the same bank/row
* each chip holds that row in its own local row buffer

So the precise hardware view is:

* one row buffer per chip

But the useful learning view is:

* the rank has a rank-wide open row

Example:

```text
per x8 chip row buffer = 1 KB
8 x8 chips in rank = 8 KB rank-wide open row
```

```text
Rank 0
+----+ +----+ +----+ +----+ +----+ +----+ +----+ +----+
|x8  | |x8  | |x8  | |x8  | |x8  | |x8  | |x8  | |x8  |
+----+ +----+ +----+ +----+ +----+ +----+ +----+ +----+

ACT(rank0, bank3, row1200)
-> every chip opens bank3,row1200
```

See:

* [[DDR - Rank relation to row buffer]]

---

## How RD works after ACT

After the row is open across the rank:

```text
RD(column)
```

makes every chip select the same column of its own active row.

For a rank of 8 x8 chips:

```text
chip0 -> 8 bits
chip1 -> 8 bits
...
chip7 -> 8 bits
```

Together:

```text
8 × 8 bits = 64 bits
```

So one column index across the rank produces one full rank-width data beat.

---

## Row hit vs row miss

If the requested row is already open in the bank:

```text
row hit
-> RD/WR directly
```

If a different row is needed in the same bank:

```text
row miss / row conflict
-> PRE current row
-> ACT new row
-> RD/WR
```

This is why open-row behavior matters for controller scheduling later.

See:

* [[DDR - Row hit vs row miss]]

---

## Summary

```text
ACT opens one row, not one bit.
The opened row is held in the sense amplifiers and called the row buffer.
Row address tells which row to open.
Column address tells which location inside that row to access.
Row buffer size is first calculated per chip.
At rank level, all chips open the same row together.
```

---

## Linked notes

* [[DDR - DRAM array hierarchy]]
* [[DDR - ACT opens a row not a bit]]
* [[DDR - Row buffer and sense amplifiers]]
* [[DDR - Row address vs column address]]
* [[DDR - Row buffer size calculation]]
* [[DDR - Rank relation to row buffer]]
* [[DDR - Row hit vs row miss]]
