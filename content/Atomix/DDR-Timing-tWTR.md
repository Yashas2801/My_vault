# tWTR - Write to Read Delay

### Definition
* Minimum delay between a **WR** command and a subsequent **RD** command.

### Question it answers
* After writing, how long must I wait before issuing a read?

### Why it exists physically
* The interface and internal DRAM logic need time to transition from write activity to read activity.
* Bus turnaround and internal write completion need spacing.

### Importance
* It protects **write-to-read turnaround**.

### Violation meaning (DV/Debug)
* If **RD** follows **WR** too quickly, the bus/internal pipeline may not be ready for the direction change.

### Quick picture
```text
WR -------- tWTR -------- RD
```

### Related notes
* [[WR writes through the active row buffer path|WR]]
* [[RD reads columns from an already open row|RD]]
* [[DDR-Timing-tWR|tWR]]
