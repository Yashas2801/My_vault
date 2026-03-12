2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

# Column access

### Definition
The action of using a `RD` (Read) or `WR` (Write) command to select a specific, small vertical slice of data from the massive, currently open Row Buffer.

### Question it answers
Once a giant row (e.g., 8,000 bits) is open, how do I get just the specific 64 bytes my CPU asked for?

### Why it exists
CPUs rarely need an entire row's worth of data at once. The Column address serves as an index to multiplex only the required bits out of the Sense Amplifiers onto the external data pins.

### Importance
`ACT` chooses the Row. `RD/WR` chooses the starting Column. You cannot issue a column access command until the row has been successfully opened and stabilized in the Row Buffer (`tRCD`).

### Related Notes
* [[DDR memory hierarchy]]
* [[RD reads columns from an already open row|RD]]
* [[WR writes through the active row buffer path|WR]]
