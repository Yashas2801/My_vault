2026-03-10 15:45
Status: #done
Tags: #ddr #vlsi #memory #timing

# tRAS - Row Active Time

### Definition
* Minimum time a row must remain open after **ACT** before a **PRE** can close it.

### Question it answers
* After opening a row with **ACT**, how long must it stay active before I can precharge the bank?

### Why it exists physically
* Once a row is activated, the cells are sensed and restored through the sense amplifiers.
* The row must remain active long enough for this restore process to complete safely.
* Closing too early can interrupt restoration.

### Importance
* It protects the **minimum safe row open time**.

### Violation meaning (DV/Debug)
* If **PRE** happens too early, the row may be closed before data restoration is complete.

### Quick picture
```text
ACT -------- tRAS -------- PRE
```

### Related notes
* [[ACT opens a row into the row buffer|ACT]]
* [[PRE closes the row and equalizes the bitlines|PRE]]
* [[DDR - Row buffer and sense amplifiers|Sense Amplifier]]
* [[DDR - Row buffer and sense amplifiers|Row Buffer]]
