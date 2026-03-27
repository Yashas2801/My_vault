2026-03-13 10:08
Status: #todo
Tags: #ddr #controller #phy #dfi #atomic-note #c1

# DFI is the internal interface between DDR controller and DDR PHY

## Statement
**DFI (DDR PHY Interface)** is the internal interface used by the DDR controller to communicate with the DDR PHY.

It is **not** the external DDR memory bus.

## Why it matters
DFI separates controller logic/protocol decisions from PHY physical execution.

## Links
- [[Controller and PHY split protocol and physical responsibilities]]
- [[DDR controller sits between AXI interconnect and DDR PHY]]
