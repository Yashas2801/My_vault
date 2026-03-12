2026-03-10 15:45
Status: #done
Tags: #ddr #vlsi #memory #timing

# tCCD - Column to Column Delay

### Definition
* Minimum delay between two column commands such as **RD-to-RD**, **WR-to-WR**, or other column command sequences, depending on the case.

### Question it answers
* After one column command, how long must I wait before issuing the next column command?

### Why it exists physically
* Column accesses share internal data path resources.
* Back-to-back column operations need spacing to avoid overlap in the column/data pipeline.

### Importance
* It protects **column command spacing**.

### Violation meaning (DV/Debug)
* If the next column command comes too early, internal column/data-path timing can be violated.

### Quick picture
```text
RD/WR -------- tCCD -------- RD/WR
```

### Related notes
* [[RD reads columns from an already open row|RD]]
* [[WR writes through the active row buffer path|WR]]
* [[DDR Commands]]
