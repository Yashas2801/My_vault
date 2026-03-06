2026-03-05 17:30

Status: #todo

Tags: #dram #refresh

## DRAM Refresh and Destructive Read

DRAM cells are dynamic, meaning they require active maintenance to preserve their data.

## Why DRAM Needs Refresh
The capacitors used in DRAM are not perfect; their electrical charge slowly **leaks** over time. If not refreshed, the voltage will drop below the threshold for a "1," resulting in data loss.

**Refresh Cycle**:
1. The memory controller periodically (typically every ~64ms) reads each row of memory.
2. The sense amplifiers restore the charge to its maximum level.
3. The row is written back.

**Interval**: Standard DDR systems refresh each row frequently to ensure data integrity.

## Destructive Read Process
Reading a DRAM cell is inherently **destructive**. When a cell is accessed:
1. The access transistor opens, connecting the capacitor to the **Bitline**.
2. The stored charge flows onto the bitline, causing a tiny voltage shift.
3. **The capacitor is now empty** (its charge has been used to perform the read).

**Sense Amplifier**:
- The sense amplifier detects the small change in bitline voltage.
- It immediately drives the bitline to full voltage (0V or $V_{DD}$).
- This **restores** the charge back into the capacitor before the row is closed.

This is why every read operation is followed by an automatic "write back" or restoration phase.
