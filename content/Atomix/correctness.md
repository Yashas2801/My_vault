---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #verification #soc
---

# Correctness

**Correctness** is the most critical dimension of SoC verification. It focuses on proving that the design functions exactly as specified under legal and intended operating conditions.

> [!info] In Simple Words
> **“Correctness means the full GPU SoC should do the right thing across compute, scheduler, PCIe, DDR, AXI, cache, and address translation.”**

---

### Core Areas of Correctness Verification

To achieve full coverage, the verification effort is divided into several specialized areas:

1. **[[dataflow-correctness|End-to-End Dataflow]]**: Verifying full-path integrity from host to GPU and back.
2. **[[scheduler-correctness|Thread Block Scheduler]]**: Ensuring workload distribution and forward progress.
3. **[[pcie-correctness|PCIe Correctness]]**: Validating host-device communication compliance.
4. **[[ddr-correctness|DDR Correctness]]**: Ensuring reliable external memory operations.
5. **[[axi-correctness|AXI Protocol Correctness]]**: Checking internal bus communication legality.
6. **[[cache-correctness|Cache Correctness]]**: Verifying data consistency and hierarchical updates.
7. **[[translation-correctness|Translation Correctness]]**: Validating address mapping and permissions.
8. **[[reset-power-clock-correctness|Reset, Clock, and Power]]**: Ensuring stability during state transitions.

---

### Summary
Ultimately, correctness verification proves that:
“When everything is used in a legal, normal way, does the whole chip behave as expected?”
