# tRCD - Row to Column Delay

### Definition
* Minimum delay between **ACT** and a subsequent **RD/WR** command to the **same bank**.

### Question it answers
* After opening a row using **ACT**, how long must I wait before issuing a **column command** (**RD** or **WR**)?

### Why it exists
* **ACT** connects the selected row to the sense amplifiers.
* The sense amplifiers need time to detect and amplify the tiny cell charge.
* The row data must become stable in the **row buffer** before column access is safe.

### Importance
* It protects **row opening and sensing**.

### Violation meaning
* If **RD/WR** is issued before **tRCD** expires, the row may not be fully sensed yet, so column access is unsafe.

### Quick Picture
```text
ACT -------- tRCD -------- RD/WR
```

### Related notes
* [[ACT opens a row into the row buffer|ACT]]
* [[DDR - Row buffer and sense amplifiers|Row Buffer & Sense Amplifiers]]
* [[DRAM Cell and Technology]]
* [[DDR Commands]]
