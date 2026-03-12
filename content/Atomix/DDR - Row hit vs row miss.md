2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #row_buffer #performance

A row hit happens when the requested access targets the row that is already open in the bank.

A row miss or row conflict happens when the request needs a different row in the same bank.

## Row hit
```text
Open row = Row 25
Request  = Row 25, Col 12

-> no new ACT needed
-> just RD/WR
```

## Row miss

```text
Open row = Row 25
Request  = Row 40, Col 7

-> PRE row 25
-> ACT row 40
-> RD/WR
```

The command model in your notes is built around this sequence: ACT opens a row, RD/WR operate on the active row, PRE closes it. 

## Why it matters

This is the first performance idea in DDR:

* same-row accesses are cheaper
* changing rows in the same bank costs more

This is why row buffer behavior later matters for controller scheduling and bank interleaving. 

## Key idea

Row locality is good.
Row switching is expensive.

## Links

* [[DDR - Row buffer and sense amplifiers]]
* [[DDR - ACT opens a row not a bit]]
* [[DRAM array and row buffer]]
