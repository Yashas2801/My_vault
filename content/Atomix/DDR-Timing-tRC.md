2026-03-10 15:45
Status: #done
Tags: #ddr #vlsi #memory #timing

# tRC - Row Cycle Time

### Definition
* Minimum delay between one **ACT** and the next **ACT** to the **same bank**.

### Question it answers
* After activating a row in one bank, how long until I can activate another row in that same bank?

### Why it exists physically
* A bank must complete its full row cycle:
  * open row
  * keep it active long enough
  * precharge and recover
* Only after that can a new row be activated in the same bank.

### Importance
* It protects the **full same-bank row-use cycle**.

### Violation meaning (DV/Debug)
* If the next **ACT** comes too soon, the previous row cycle may not be fully completed.

### Quick picture
```text
ACT -------------------- tRC -------------------- ACT
```

### Related notes
* [[ACT opens a row into the row buffer|ACT]]
* [[DDR-Timing-tRAS|tRAS]]
* [[DDR-Timing-tRP|tRP]]
* [[DDR - DRAM array hierarchy|Bank]]
