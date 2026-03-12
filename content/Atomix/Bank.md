2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

# Bank

### Definition
The core independent working unit inside a DRAM chip, containing its own memory array, row decoders, column decoders, and a dedicated Row Buffer (Sense Amplifiers).

### Question it answers
Where does the actual activation of a memory row happen independently?

### Why it exists
To allow the DRAM chip to process multiple memory requests concurrently. While one Bank is busy opening a row, another Bank can be actively sending data to the CPU.

### Importance
**Rule:** One bank can only have ONE active row open at a time. 
If the controller needs data from a different row in the same bank, it suffers a performance penalty because it must close the old row (`PRE`) before opening the new one (`ACT`).

### Related Notes
* [[DDR memory hierarchy]]
* [[Row buffer]]
* [[PRE closes the row and equalizes the bitlines|PRE]]
