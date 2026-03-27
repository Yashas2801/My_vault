2026-03-13 10:10
Status: #todo
Tags: #ddr #phy #sodimm #atomic-note #c1

# DDR PHY drives the external DDR4 SoDIMM interface

## Statement
The external SoDIMM is driven by the **PHY**, not directly by the controller.

## Path
`DDR controller -> DDR PHY -> SoDIMM`

## Why it matters
This prevents a common confusion: the controller does not directly handle the board-level DDR electrical interface. That is mainly the PHY’s role.

## Links
- [[Controller and PHY split protocol and physical responsibilities]]
- [[DDR controller sits between AXI interconnect and DDR PHY]]
