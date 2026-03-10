2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #addressing

A memory request is not used as one flat number inside DRAM.
The controller maps it into fields such as:

```text
Rank / Bank / Row / Column
```

A row address means:
which row number inside the selected bank should be opened

A column address means:
which position inside the already-open row should be accessed

## Visual

```text
Address -> Rank / Bank / Row / Column

ACT uses: bank + row
RD/WR use: column
```

## Example

```text
Rank   = 0
Bank   = 3
Row    = 1200
Column = 64
```

This means:

* ACT opens row 1200 in bank 3
* RD/WR later use column 64 within that active row

The controller command sequence in your notes explicitly follows this model: ACT selects bank+row, then RD/WR select a column within the active row. 

## Key idea

Row address = which row to open
Column address = which place inside that open row to access

## Links

* [[DDR - ACT opens a row not a bit]]
* [[DDR - DRAM array hierarchy]]
* [[DDR - Rank relation to row buffer]]
* [[Stage 1.3 - DRAM array and row buffer]]
