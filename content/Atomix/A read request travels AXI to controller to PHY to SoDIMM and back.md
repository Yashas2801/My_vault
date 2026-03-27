2026-03-13 10:14
Status: #todo
Tags: #ddr #controller #read-path #atomic-note #c1

# A read request travels AXI to controller to PHY to SoDIMM and back

## Statement
A read request moves through multiple interfaces and blocks in a specific sequence.

## Path
1. Requester issues read.
2. AXI interconnect carries request.
3. Controller accepts request.
4. Controller translates it into DDR-side intent.
5. Controller sends intent through DFI.
6. PHY drives the external DDR interface.
7. SoDIMM returns data.
8. PHY captures data.
9. Controller returns data on AXI side.

## Links
- [[AXI side presents memory requests to the DDR controller]]
- [[DFI is the internal interface between DDR controller and DDR PHY]]
- [[DDR PHY drives the external DDR4 SoDIMM interface]]
