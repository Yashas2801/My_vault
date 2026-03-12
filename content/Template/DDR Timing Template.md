2026-03-10 15:45
Status: #todo
Tags: #ddr #vlsi #memory #timing

# {{title}} - [Full Name]

### Definition
* Minimum delay between **[Command A]** and a subsequent **[Command B]** to the **[same/different] bank/rank**.

### Question it answers
* After issuing **[Command A]**, how long must I wait before I can safely issue **[Command B]**?

### Why it exists physically
* [Physical reason 1: e.g., Sense amplifiers need time to stabilize]
* [Physical reason 2: e.g., Precharging the bitlines to VDD/2]
* [Physical reason 3: e.g., Data bus turnaround time]

### Importance
* It protects **[what physical process: e.g., row closing, data integrity, bus contention]**.

### Violation meaning (DV/Debug)
* If **[Command B]** is issued before **{{title}}** expires, **[consequence: e.g., data corruption, illegal command state, bus collision]** occurs.

### Quick Picture
```text
[CMD A] -------- {{title}} -------- [CMD B]
```

### Not to confuse with:
* [[Other Timing]] - [Brief distinction]

### Related notes
* [[DDR Commands]]
* [[DDR - DRAM array hierarchy]]
* [[DDR SDRAM Index]]
