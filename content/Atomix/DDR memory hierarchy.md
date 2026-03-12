2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

# DDR memory hierarchy

### Definition
The structural organization of DDR memory from the outside system view down to the actual storage location inside the silicon.

### Order
* Channel -> Rank -> Chip -> Bank Group -> Bank -> Row -> Column

### Question it answers
When a system issues a memory address, where exactly does that request physically go inside the DRAM architecture?

### Why it exists
* To build large-capacity memory from many small cells.
* To allow maximum parallelism across independent channels, ranks, bank groups, and banks.
* To support row-buffer based access instead of slow, direct cell-by-cell access.

### Importance
* Explains the required sequence of commands (`ACT` -> `RD/WR` -> `PRE`).
* Explains row hits vs. row misses (performance variations).
* Explains how bandwidth is scaled using physical hierarchy and parallelism.

### Related Notes
* [[DDR Memory Hierarchy]]
* [[DDR Commands]]
