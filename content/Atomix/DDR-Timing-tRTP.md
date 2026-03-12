# tRTP - Read to Precharge Delay

### Definition
* Minimum delay between a **RD** command and a subsequent **PRE** to that bank.

### Question it answers
* After a read, how long must I wait before closing the row?

### Why it exists physically
* The read operation must complete safely before the bank is closed.
* The row cannot be precharged while the read still depends on that open-row state.

### Importance
* It protects **read completion before row close**.

### Violation meaning (DV/Debug)
* If **PRE** is issued too early after **RD**, the read operation may be cut off before safe completion.

### Quick picture
```text
RD -------- tRTP -------- PRE
```

### Related notes
* [[RD reads columns from an already open row|RD]]
* [[PRE closes the row and equalizes the bitlines|PRE]]
* [[DDR-Timing-tWR|tWR]]
