2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #act #row_buffer

## Statement
ACT opens a selected row in a selected bank and loads that row into the sense amplifiers / row buffer.

## Why it matters
DDR cannot read or write arbitrary columns in a bank unless the row is first active.

## Mini visual
```text
Before ACT:
closed row

After ACT:
row <-> row buffer
```

## Links

* [[1.4 DDR Command Model]]
* [[RD reads columns from an already open row]]
* [[WR writes through the active row buffer path]]
* [[PRE closes the row and equalizes the bitlines]]
