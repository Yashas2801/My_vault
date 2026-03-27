---
date: 2026-03-27 13:34
status: #done
tags: #gpu #compilation #binary #metadata
---

# Compiling Kernels

**Compiling kernels** is the process of converting kernel source code into device-executable binary code that the GPU hardware can understand.

### The Conversion Process
The runtime resolves the kernel’s device binary (e.g., **PTX**, **SASS**, **GCN**, **SPIR-V**) and extracts vital metadata required for execution:
- **Register usage**: How many hardware registers each thread requires.
- **Shared memory usage**: Amount of on-chip memory needed per block.
- **Alignment**: Memory alignment requirements for arguments and data.
- **Occupancy constraints**: Limits on how many blocks can run concurrently on a single SM.

> [!info] In Simple Words
> **“Turn the kernel program into something the GPU can actually execute, and collect the info needed to launch it correctly.”**

---

> [!tip] Presentation Summary
> For a high-level overview, you can summarize this as:
> *“Compiling means preparing GPU-executable kernel code and its associated metadata.”*
