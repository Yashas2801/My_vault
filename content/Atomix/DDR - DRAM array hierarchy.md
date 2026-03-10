2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #architecture

A DRAM chip is organized hierarchically.

```text
Channel
  -> Module / DIMM / SoDIMM
    -> Rank
      -> Chip
        -> Bank Group
          -> Bank
            -> Row
              -> Column
```

For Stage 1.3, the most important part is inside a bank:

```text
Bank
  -> many rows
  -> each row has many columns
```

A row is a horizontal line of cells.
A column is a position within that row.

When a bank is activated, one full row in that bank becomes active. This is the bridge between DRAM cell physics and DDR command behavior. Stage 1.3 in the roadmap is specifically about learning rows, columns, wordlines, bitlines, sense amplifiers, row buffer, and open-row behavior. 

## Key idea

Memory access is not “pick one isolated bit directly from the whole chip”.
It is usually:

1. choose bank
2. open row
3. select column within the open row

## Links

* [[DDR - ACT opens a row not a bit]]
* [[DDR - Row buffer and sense amplifiers]]
* [[DDR - Row address vs column address]]
* [[Stage 1.3 - DRAM array and row buffer]]
