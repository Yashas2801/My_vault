2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

# Rank

### Definition
A group of multiple DRAM chips on a memory module (DIMM) that share a chip-select signal and are accessed together to form one single, wider data bus.

### Question it answers
How do we get a 64-bit wide data bus when individual DRAM chips are only 4, 8, or 16 bits wide?

### Why it exists
Individual memory chips are too narrow to efficiently feed modern 64-bit CPU buses. By grouping (for example) eight `x8` chips together into a Rank, the memory controller can read/write 64 bits simultaneously.

### Importance
A rank is the foundational unit of parallel chip access. 
**Crucial Distinction:** A rank is *not* one chip. A rank is a team of chips working in unison.

### Related Notes
* [[DDR memory hierarchy]]
* [[Burst length]]
