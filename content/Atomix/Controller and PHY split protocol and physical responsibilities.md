2026-03-13 10:09
Status: #todo
Tags: #ddr #controller #phy #atomic-note #c1

# Controller and PHY split protocol and physical responsibilities

## Statement
The controller and PHY do different jobs in the DDR system.

### Controller
Responsible for:
- deciding what operation should happen
- deciding when it is legal
- scheduling commands
- obeying protocol/timing rules

### PHY
Responsible for:
- electrical signaling
- DQ/DQS timing
- launch and capture
- training and calibration behavior

## Why it matters
This split allows the logic designer to focus on protocol and the physical designer to focus on electrical integrity.

## Links
- [[DFI is the internal interface between DDR controller and DDR PHY]]
- [[DDR PHY drives the external DDR4 SoDIMM interface]]
