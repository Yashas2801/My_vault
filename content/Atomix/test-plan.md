---
date: 2026-03-27 13:34
status: #done
tags: #dv #verification #gpu #soc
---

# Test Plan

A **test plan** is the comprehensive list of items the Design Verification (DV) team intends to verify. It serves as the primary roadmap for the verification effort.

### Core Objectives
It answers the fundamental questions:
- **Which features** must be tested?
- **What scenarios** must be executed?
- **What does good behavior** look like?
- **What bad/error cases** must be checked?

> [!info] In Simple Words
> It is a **checklist of verification targets**.

---

### Verification Targets
For a GPU SoC, the test plan includes features such as:
- [ ] **End-to-end dataflow**
- [ ] **Host-to-GPU PCIe path**
- [ ] **GPU-to-host path**
- [ ] **Thread block scheduler**
- [ ] **DDR correctness**
- [ ] **AXI correctness**
- [ ] **Cache correctness**
- [ ] **MMU/TLB translation correctness**
- [ ] **Reset/power/clock behavior**
- [ ] **Robustness cases**: Resets during traffic and error propagation

---

> [!example] Anatomy of a Test Plan Entry
> **Feature**: Inbound PCIe DMA
> **What to test**: Host writes data into GPU-accessible memory
> **Expected result**: Data reaches correct destination, no protocol error
> **Corner cases**: Wrong address, partial transfer, reset in between

### Conclusion
Ultimately, the test plan defines the scope:
> “For this feature, these are the scenarios we **must** test.”
