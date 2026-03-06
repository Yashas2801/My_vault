2026-03-05 17:30

Status: #done

Tags: #ddr

## What is DDR SDRAM

**DOUBLE DATA RATE SYNCHRONOUS DYNAMIC RANDOM ACCESS MEMORY**

**DOUBLE DATA RATE**
- The data transfer happens in both the clock edges, i.e(both pos edge and neg edge) of clk.
- For the same frequency, the bandwidth is doubled.

**DYNAMIC** vs **STATIC**

| Feature             | Dynamic                                  | Static                                       |
| :------------------ | :--------------------------------------- | :------------------------------------------- |
| **Storage Element** | Capacitor (requires periodic refreshing) | Flip-Flop / Latches (no refreshing required) |
| **Speed**           | Slower                                   | Faster                                       |
| **Density**         | Higher (more compact)                    | Lower (requires more transistors per bit)    |
- Since static RAMs are very fast, they don't require DDR protocol to increase it's speed
- DRAMs are preferred for external memory since they are cheap to produce and more memory can be packed in a single chip (**High Density**)