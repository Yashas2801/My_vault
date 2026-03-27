---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #scheduler #gpu #sm
---

# Thread Block Scheduler Correctness

**Thread Block Scheduler Correctness** verifies that the GPU's scheduling machinery assigns work properly and ensures the workload progresses through the execution units as intended.

### Core Requirements
- **Forward Progress**: Every block and its constituent threads must continue to execute without getting stuck.
- **Resource Constraints**: The scheduler must respect limits on registers, shared memory, and thread counts.
- **Semantics**: Adherence to **SIMT** (Single Instruction, Multiple Threads) and barrier synchronization rules.
- **Saturation**: The workload should properly saturate the SPs, then SMs, then clusters to maximize throughput.

> [!info] In Simple Words
> It is not enough to say “a kernel launched.” We must check if the scheduler is actually handing out work and if the blocks are progressing toward completion.

---

> [!example] Scheduling Scenario
> If 100 thread blocks are launched:
> - Are they distributed correctly across available SMs?
> - When one block finishes, is a new one immediately picked up?
> - Do synchronization barriers correctly pause and resume execution?
