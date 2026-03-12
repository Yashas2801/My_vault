2026-03-10 15:45
Status: #done
Tags: #ddr #vlsi #memory #timing

# tWR - Write Recovery Time

### Definition
* Minimum delay after a **WR** before a **PRE** can be issued to that bank.

### Question it answers
* After a write, how long must I wait before closing the row?

### Why it exists physically
* Write data must be safely stored back into the memory cells.
* The row cannot be closed immediately after the write command/data burst.
* DRAM needs recovery time to complete write restoration.

### Importance
* It protects **write completion before row close**.

### Violation meaning (DV/Debug)
* If **PRE** occurs too early after **WR**, the write may not be fully restored into the cells.

### Quick picture
```text
WR -------- tWR -------- PRE
```

### Related notes
* [[WR writes through the active row buffer path|WR]]
* [[PRE closes the row and equalizes the bitlines|PRE]]
* [[DDR-Timing-tRTP|tRTP]]
