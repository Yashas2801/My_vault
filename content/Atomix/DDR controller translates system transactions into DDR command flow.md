2026-03-13 10:07
Status: #todo
Tags: #ddr #controller #atomic-note #c1

# DDR controller translates system transactions into DDR command flow

## Statement
A major job of the DDR controller is to convert high-level memory requests into legal DDR command sequences.

## Abstraction difference
System side speaks in:
- requests
- addresses
- bursts
- responses

DDR side speaks in:
- ACT
- RD
- WR
- PRE
- REF
- timing constraints

## Why it matters
This is the core reason the controller exists. It bridges AXI transaction semantics and DDR command/timing semantics.

## Links
- [[AXI side presents memory requests to the DDR controller]]
- [[DDR controller internally contains arbitration scheduling and command generation]]
