---
date: 2026-03-27 13:34
status: #done
tags: #gpu #driver #runtime #host-interface
---

# Driving Kernels

**Driving kernels** means feeding the prepared kernel request into the SoC through the verification environment or host software path.

### The Software Path
Unlike simple traffic generation, "driving" involves the full software stack:
1. **Argument Packing**: The runtime packs arguments into a parameter buffer.
2. **Validation**: Grid and block settings are checked for hardware compatibility.
3. **System Call**: The runtime notifies the GPU driver with kernel handles and execution configurations.
4. **Command Generation**: The driver constructs hardware-level **command buffers** in GPU-visible memory.
5. **Hardware Notification**: The driver writes to a **doorbell register** or updates a **queue tail pointer** to alert the GPU of new work.

> [!info] In Simple Words
> **“Driving means pushing the kernel launch information from the host side into the GPU system in the way real software would.”**

---

### Key Verification Steps
In a DV environment, this involves:
- [x] **Program setup**
- [x] **Buffer preparation**
- [x] **Launch request submission**
- [x] **Doorbell/Queue signaling**
