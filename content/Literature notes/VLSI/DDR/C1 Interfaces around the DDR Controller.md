2026-03-13 10:00
Status: #todo
Tags: #ddr #controller #c1 #literature-note

# C1 — Interfaces around the DDR Controller

## Core idea
The DDR controller is the boundary translator between the SoC memory-request world and the DDR memory-operation world.

In this project architecture, the **DDR4 Memory Controller** sits between the **Non-Cache Coherent Interconnect (AXI4)** and the **DDR4 PHY**. The PHY then connects to the external **SoDIMM**. This means the controller does not directly drive the memory pins. Instead, it translates system-side requests into DDR-side command intent and passes that intent to the PHY.

## System-side interface
On the SoC side, the controller receives **AXI4 transactions**.

These are not raw DRAM commands like ACT, RD, WR, or PRE. They are higher-level memory requests such as:
- read requests
- write requests
- addresses
- bursts
- write data
- responses

So the AXI side is a **transaction interface**, not a DRAM command interface.

See:
- [[AXI side presents memory requests to the DDR controller]]
- [[DDR controller translates system transactions into DDR command flow]]

## Controller-to-PHY interface
The controller talks to the PHY using **DFI**.

**DFI = DDR PHY Interface**

This is the internal controller–PHY interface, not the external DDR bus. Through DFI, the controller conveys command and data intent, and the PHY performs the physical execution.

See:
- [[DFI is the internal interface between DDR controller and DDR PHY]]
- [[Controller and PHY split protocol and physical responsibilities]]

## PHY and external memory
The PHY is the block that handles the real DDR interface toward the external memory module.

So the external path is:

`AXI4 interconnect -> DDR controller -> DFI -> DDR PHY -> SoDIMM`

This means:
- controller = logic/protocol/timing decision block
- PHY = electrical/pin-level execution block

See:
- [[DDR PHY drives the external DDR4 SoDIMM interface]]

## Configuration and bring-up interfaces
Besides the AXI data path, the controller also depends on:
- a **configuration interface** for register programming
- **clock and reset** for bring-up and safe operation

The controller’s operating behavior depends on these supporting interfaces before normal traffic begins.

See:
- [[DDR controller is programmed through configuration registers]]
- [[DDR controller depends on clock and reset sequencing]]

## Internal meaning of the controller block
The controller is not a passive bridge. Internally, it contains logic for:
- arbitration
- scheduling
- DDR command generation

This means requests come in on AXI, then the controller decides:
1. which request to serve
2. when it is legal to serve it
3. what DDR command sequence must be produced

See:
- [[DDR controller internally contains arbitration scheduling and command generation]]

## End-to-end read mental model
A read request flows like this:

1. A requester generates a memory read
2. The request enters the AXI interconnect
3. The DDR controller accepts the request
4. The controller translates it into DDR command intent
5. The controller sends intent to the PHY through DFI
6. The PHY drives the external DDR interface
7. Data returns from the SoDIMM
8. PHY captures it
9. Controller returns it as AXI read data

See:
- [[A read request travels AXI to controller to PHY to SoDIMM and back]]

## Final summary
C1 can be remembered as:

- **AXI4** brings requests in
- **APB/config path** programs controller behavior
- **DFI** connects controller to PHY
- **PHY** drives the real DDR interface toward the SoDIMM

## Backlinks
- [[C0 What is the DDR Controller in my ASIC]]
- [[C2 Internal Controller Pipeline]]
