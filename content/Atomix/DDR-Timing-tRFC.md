# tRFC - Refresh Cycle Time

### Definition
* Minimum time the DRAM remains busy after a **REF** command before normal access commands can resume.

### Question it answers
* After a refresh, how long must the controller wait before issuing normal commands again?

### Why it exists physically
* Refresh restores charge in DRAM cells.
* During refresh, the array is busy and not available for ordinary accesses.
* DRAM needs time to complete the refresh operation safely.

### Importance
* It protects **refresh completion**.

### Violation meaning (DV/Debug)
* If normal commands resume too early after refresh, the device may still be busy with refresh activity.

### Quick picture
```text
REF -------- tRFC -------- ACT/RD/WR allowed
```

### Related notes
* [[REFRESH is mandatory because DRAM cells leak|Refresh]]
* [[DDR Commands]]
