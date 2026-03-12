2026-03-10 15:45
Status: #done
Tags: #ddr #vlsi #memory #timing

# CL - CAS Latency

### Definition
* Minimum delay between a **RD** command and the appearance of the **first data** on the data bus.

### Question it answers
* After issuing **RD**, how long must I wait before the first read data appears?

### Why it exists physically
* A read command selects columns from the already-open row.
* The DRAM internal data path needs time to move the selected data to the output.
* Only after this delay does the first valid data appear on the bus.

### Importance
* It protects the **read data return timing**.

### Violation meaning (DV/Debug)
* If data is assumed too early, the read data may not yet be valid.

### Quick picture
```text
RD -------- CL -------- D0
```

### Related notes
* [[RD reads columns from an already open row|RD]]
* [[DDR-Timing-tRCD|tRCD]]
* [[DDR Commands]]
