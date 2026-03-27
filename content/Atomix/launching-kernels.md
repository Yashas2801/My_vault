---
date: 2026-03-27 13:34
status: #done
tags: #gpu #execution #dispatch #hardware
---

# Launching Kernels from Host

**Launching kernels** is the final step where the host successfully hands over the work, and the GPU begins physical processing and execution.

### The Execution Handover
Once the host submits the request, the hardware takes over:
1. **Handover**: The host completes its submission tasks.
2. **Command Fetch**: The GPU front end reads the commands from memory.
3. **Dispatch**: The dispatch unit breaks the global grid into individual thread blocks.
4. **Scheduling**: The scheduler assigns these blocks to available Streaming Multiprocessors (SMs).
5. **Execution**: The SMs begin processing threads.
6. **Completion**: A signal (interrupt, event, or memory update) is sent back to the host.

> [!info] In Simple Words
> **“Launching means the host has successfully handed over the work, and the GPU begins processing it.”**

---

### Hardware/Software Boundary
- **Host Responsibility**: Preparing command buffers and updating pointers.
- **GPU Responsibility**: Fetching, decoding, scheduling, and executing the workload.
