# tRP - Row Precharge Time

### Definition
* Minimum delay between **PRE** and the next **ACT** to the **same bank**.

### Question it answers
* After closing a bank with **PRE**, how long must I wait before opening another row in that bank?

### Why it exists physically
* PRE closes the currently open row.
* The bank’s bitlines and sensing structures must return to their neutral/precharged state.
* Only then is it safe to activate a new row.

### Importance
* It protects **bank closing and reset**.

### Violation meaning (DV/Debug)
* If **ACT** is issued too early after **PRE**, the bank may not be ready to open the next row safely.

### Quick picture
```text
PRE -------- tRP -------- ACT
```

### Related notes
* [[PRE closes the row and equalizes the bitlines|PRE]]
* [[ACT opens a row into the row buffer|ACT]]
* [[DDR - DRAM array hierarchy|Bank]]
* [[DDR-Timing-tRC|tRC]]
