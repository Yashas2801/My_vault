2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

# Burst length

### Definition
The number of consecutive data transfers (beats) transmitted back-to-back on the data bus resulting from a single `RD` or `WR` column command.

### Question it answers
Does DDR send just one single piece of data per command and stop?

### Why it exists
To maximize data bus efficiency. Sending commands (addressing) over the bus takes time. Once the memory location is located, it is significantly faster to continuously burst a chunk of sequential data out than to ask for it bit by bit.

### Importance
In DDR4, the standard burst length is 8 (BL8). 
**Calculation:** A 64-bit wide Rank bursting 8 times yields: `64 bits × 8 beats = 512 bits = 64 Bytes` per single read command.

### Related Notes
* [[Rank]]
* [[Column access]]
* [[DDR memory hierarchy]]
