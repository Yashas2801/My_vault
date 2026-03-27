2026-03-13 10:05
Status: #todo
Tags: #ddr #controller #atomic-note #c1

# DDR controller sits between AXI interconnect and DDR PHY

## Statement
In this project, the DDR controller sits between the **AXI4 interconnect** and the **DDR4 PHY**.

It acts as the logical bridge between:
- the SoC transaction world
- the DDR protocol world

## Why it matters
This placement explains why the controller does not directly talk to the SoDIMM pins.

The path is:
`AXI4 -> DDR controller -> DDR PHY -> SoDIMM`

## Links
- [[AXI side presents memory requests to the DDR controller]]
- [[DFI is the internal interface between DDR controller and DDR PHY]]
- [[DDR PHY drives the external DDR4 SoDIMM interface]]
