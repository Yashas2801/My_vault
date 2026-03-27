2026-03-13 10:13
Status: #todo
Tags: #ddr #controller #scheduler #arbiter #atomic-note #c1

# DDR controller internally contains arbitration scheduling and command generation

## Statement
The controller is an active decision-making block. Internally it performs:
1. **Arbitration**: Choosing between multiple requesters.
2. **Scheduling**: Ordering requests for maximum efficiency.
3. **Command Generation**: Creating the legal DDR command stream.

## Why it matters
This explains how the controller turns many incoming requests into a legal and efficient DRAM command stream while obeying all timing constraints.

## Links
- [[DDR controller translates system transactions into DDR command flow]]
- [[C2 Internal Controller Pipeline]]
