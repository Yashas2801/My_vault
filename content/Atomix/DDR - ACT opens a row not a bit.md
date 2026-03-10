2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #act #row_buffer

A common beginner mistake is to think DDR reads one bit at a time because the storage cell stores one bit.

That is not how ACT works.

ACT does not open one bit.
ACT does not open one column.
ACT opens one whole row in the selected bank.

```text
Closed bank
   |
   | ACT(bank, row)
   v
Open row in that bank
```

The DDR command model says:

* ACT selects a bank and a row
* DRAM loads that row into the sense amplifiers
* RD/WR later select columns within that active row 

## Why this matters

This is why DDR access is naturally two-step:

1. row selection
2. column access

## Visual

```text
Bank 3
+----------------------------------+
| Row 0    [ .... columns .... ]   |
| Row 1    [ .... columns .... ]   |
| Row 2    [ .... columns .... ]   |
| ...                              |
| Row 1200 [ .... columns .... ]   | <- ACT opens this whole row
| ...                              |
+----------------------------------+
```

## Key idea

ACT opens a row.
RD/WR use the open row.

## Links

* [[DDR - Row buffer and sense amplifiers]]
* [[DDR - Row address vs column address]]
* [[DDR - Row hit vs row miss]]
* [[Stage 1.3 - DRAM array and row buffer]]
