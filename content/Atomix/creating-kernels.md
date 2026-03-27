---
date: 2026-03-27 13:34
status: #done
tags: #gpu #programming #kernel #host
---

# Creating Kernels

**Creating kernels** involves writing or preparing the specific GPU work that you want to execute. It defines the "what" and "where" of the computation.

### Application-Level Specifications
When a host application creates a kernel, it specifies several key parameters:
- **Kernel function**: The actual code to be executed on the GPU.
- **Grid dimensions**: The total number of thread blocks.
- **Block dimensions**: The number of threads within each block.
- **Kernel arguments**: The data inputs the kernel will process.
- **Stream / Command queue**: The execution context for the kernel.

> [!info] In Simple Words
> It answers: **“What work should the GPU do, on how much data, and with what launch settings?”**

---

### Core Components
- **Workload Definition**: Selecting the algorithm and data structures.
- **Configuration**: Mapping the problem size to the GPU's hierarchical thread model (Grids and Blocks).
- **Argument Setup**: Preparing the pointers and values the GPU will need to access.
