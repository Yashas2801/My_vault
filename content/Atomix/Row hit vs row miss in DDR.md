2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #row_buffer #performance

## Statement
A **row hit** occurs when the requested row is already open, allowing immediate RD/WR. A **row miss** occurs when a different row is needed in the same bank, requiring a PRE followed by an ACT.

## Why it matters
Controller performance depends heavily on this. Hitting the open row saves the time penalty of closing and reopening rows.

## Mini visual
```text
Row Hit:
Open = row 100
Req  = row 100, col 40 -> RD/WR directly

Row Miss:
Open = row 100
Req  = row 220 -> PRE -> ACT row 220 -> RD/WR
```

## Links

* [[1.4 DDR Command Model]]
* [[ACT opens a row into the row buffer]]
* [[PRE closes the row and equalizes the bitlines]]
