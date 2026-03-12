2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #read

## Statement
RD does not open a new row. It selects columns from an already active row. Data appears after the specified read latency, followed by a data burst.

## Why it matters
Understanding that RD operates *only* on an open row is crucial to the two-step (ACT -> RD) memory access model.

## Mini visual
```text
ACT opens row 100
RD col 20 reads from row 100, col 20 onward (burst)
```

## Links

* [[DDR Command Model]]
* [[ACT opens a row into the row buffer]]
* [[WR writes through the active row buffer path]]
