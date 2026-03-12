# tRRD - Row to Row Delay

### Definition
* Minimum delay between two **ACT** commands to different banks.

### Question it answers
* After activating one bank, how long must I wait before activating another bank?

### Why it exists physically
* ACT is a power-intensive operation.
* Multiple row activations too close together increase instantaneous current demand.
* DRAM limits how densely activations can be issued.

### Importance
* It protects **multi-bank activation spacing**.

### Violation meaning (DV/Debug)
* If ACTs are issued too closely, the device may exceed safe internal activation limits.

### Quick picture
```text
ACT(bank0) -------- tRRD -------- ACT(bank1)
```

### Related notes
* [[ACT opens a row into the row buffer|ACT]]
* [[DDR - DRAM array hierarchy|Bank]]
* [[DDR-Timing-tFAW|tFAW]]
