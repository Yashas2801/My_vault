2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #rank #row_buffer

A rank is a group of DRAM chips that share the same chip select and are accessed together as one logical unit. In DDR4, a common rank width is 64 bits.

## Important distinction
Per-chip row buffer and rank-wide open row are not the same thing.

Each chip has its own local row buffer.
But when a rank is selected and ACT is issued, all chips in that rank open the same bank/row together.

## Visual
```text
Rank 0
+----+ +----+ +----+ +----+ +----+ +----+ +----+ +----+
|x8  | |x8  | |x8  | |x8  | |x8  | |x8  | |x8  | |x8  |
+----+ +----+ +----+ +----+ +----+ +----+ +----+ +----+

ACT(rank0, bank3, row1200)

-> every chip opens bank3,row1200
-> each chip holds that row in its own row buffer
```

## Example

For one x8 chip with 1K columns:

```text
row buffer per chip = 1 KB
```

For a rank made of 8 x8 chips:

```text
rank width = 8 × 8 = 64 bits
rank-wide open row = 8 × 1 KB = 8 KB
```

Equivalent calculation:

```text
1024 columns × 64 bits = 65536 bits = 8192 bytes = 8 KB
```

## What RD does

After ACT:

* each chip already has the same row open
* RD(column) makes every chip select that same column
* all chips contribute their bits together
* the rank returns the full data width

## Key idea

A rank does not have one single physical row buffer.
It has one row buffer per chip, but together they behave like one rank-wide open row.

## Links

* [[DDR - Row buffer size calculation]]
* [[DDR - Row address vs column address]]
* [[DDR - ACT opens a row not a bit]]
* [[DRAM array and row buffer]]
