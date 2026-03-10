2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #write

## Statement
WR requires an active row. The write goes through the active row-buffer path, and data is restored into the cells of the open row. WR is *not* a bypass around ACT.

## Why it matters
It corrects the misconception that writes go directly to closed cells. Both reads and writes must pass through the row buffer.

## Mini visual
```text
ACT:
cell array row -> row buffer

WR:
controller data -> selected columns in row buffer path -> cells of open row
```

## Links

* [[1.4 DDR Command Model]]
* [[ACT opens a row into the row buffer]]
* [[RD reads columns from an already open row]]
