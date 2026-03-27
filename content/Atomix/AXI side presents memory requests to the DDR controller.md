2026-03-13 10:06
Status: #todo
Tags: #ddr #controller #axi #atomic-note #c1

# AXI side presents memory requests to the DDR controller

## Statement
On the SoC side, the DDR controller receives **AXI4 transactions**.

These include:
- read requests
- write requests
- addresses
- burst information
- write data
- responses

## Key clarification
The AXI side does **not** send raw DRAM commands such as:
- ACT
- RD
- WR
- PRE

It sends higher-level memory transactions.

## Why it matters
This shows that the controller must translate between system-level requests and DRAM-level command sequences.

## Links
- [[DDR controller translates system transactions into DDR command flow]]
- [[DDR controller sits between AXI interconnect and DDR PHY]]
