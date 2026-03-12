2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #row_buffer

The row buffer is the practical result of activation.

When ACT opens a row, the selected row connects to the bitlines, and the sense amplifiers detect and amplify the tiny signal from the cells. The sense amplifiers then hold the opened row. This held row is what we call the row buffer.

## Mental model
```text
Cell data is weak
Sense amp makes it strong
Sense amp holds the open row
```

## Visual

```text
Before ACT:
  cells store weak charge
  no selected row is active

After ACT:
  selected row -> bitlines -> sense amplifiers
  sense amplifiers now hold the row
  this held row = row buffer
```

## Why row buffer matters

Once the row is open in the row buffer:

* RD can select a column from it
* WR can update a column in it
* more accesses to the same row are cheaper than switching rows

## Key idea

Row buffer is not a CPU-style cache.
It is the active row currently held by the sense amplifiers.

## Links

* [[DDR - ACT opens a row not a bit]]
* [[DDR - Row buffer size calculation]]
* [[DDR - Rank relation to row buffer]]
* [[DDR - Row hit vs row miss]]
* [[DRAM array and row buffer]]
