2026-03-13 10:11
Status: #todo
Tags: #ddr #controller #config #atomic-note #c1

# DDR controller is programmed through configuration registers

## Statement
The controller is not only a traffic block. It also has configuration registers that must be programmed before proper operation.

## Why it matters
The controller needs programmed values for things like:
- timing parameters
- address mapping
- refresh behavior
- operating mode choices

## Key distinction
- **AXI path**: traffic path
- **Config/register path**: programming path

## Links
- [[DDR controller depends on clock and reset sequencing]]
- [[C1 Interfaces around the DDR Controller]]
