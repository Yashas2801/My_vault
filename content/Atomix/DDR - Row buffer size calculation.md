2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #row_buffer

Row buffer size means:
how much data is present in one opened row of one chip

## Formula
```text
row buffer size = number of columns in a row × chip width
```

If you want bytes:

```text
row buffer bytes = (columns × chip width) / 8
```

## Example 1: x8 chip with 1K columns

```text
1K columns = 1024 columns
chip width = 8 bits

row buffer size = 1024 × 8 bits
                = 8192 bits
                = 1024 bytes
                = 1 KB
```

## Example 2: x4 chip with 1K columns

```text
row buffer size = 1024 × 4 bits
                = 4096 bits
                = 512 bytes
```

## Example 3: x16 chip with 1K columns

```text
row buffer size = 1024 × 16 bits
                = 16384 bits
                = 2048 bytes
                = 2 KB
```

## Visual

```text
x8 chip row

C0      C1      C2      ...     C1023
[8 bits][8 bits][8 bits]...     [8 bits]

Total = 1024 × 8 bits = 1 KB
```

## Important clarification

“1K columns” does not mean one bit per column for the whole chip.
It means 1024 column positions.
Each position contributes chip-width bits.

## Key idea

The row buffer calculation is first done per chip, not per rank.

## Links

* [[DDR - Row buffer and sense amplifiers]]
* [[DDR - Rank relation to row buffer]]
* [[DRAM array and row buffer]]
