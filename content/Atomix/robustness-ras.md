---
date: 2026-03-27 13:34
status:
tags:
---

# Robustness & RAS

While **Correctness** asks “does it work normally?”, **Robustness** asks: **“What happens if something goes wrong?”** 

This dimension ensures the SoC behaves safely and predictably under stress, faults, or illegal conditions.

### Verification Scope
The robustness plan includes:
- **Resets during traffic**: Handling asynchronous reset signals while data is in flight.
- **Hot/Surprise PCIe Resets**: Managing sudden link losses or host-initiated resets.
- **Link Retrain**: Ensuring the system recovers if a high-speed link (like PCIe) needs to retrain.
- **NoC Backpressure Extremes**: Testing the limits of internal interconnect congestion.
- **Protocol Errors**: Validating error detection and reporting for AXI, PCIe, DDR, and TLB.
- **Isolation & Permissions**: Ensuring illegal accesses are blocked and don't affect unrelated blocks.

> [!info] In Simple Words
> This part checks whether the chip behaves safely and predictably under stress or faults.

---

### Expected Behavior under Stress
When a fault or corner case occurs (e.g., memory stalls badly, bad address accessed), the system must guarantee:
1. **No Deadlock**: The system must not hang indefinitely.
2. **No Random Corruption**: Errors must not silently corrupt unrelated data.
3. **Proper Reporting**: The error must be flagged to the host or a status register.
4. **Safe Failure**: The system either recovers or fails in a "clean" way that allows for a predictable restart.

> [!example] Robustness Scenarios
> - A reset happens exactly when a DDR write is being acknowledged.
> - A PCIe link drops and comes back in the middle of a large DMA transfer.
> - A kernel tries to access a memory region it doesn't have permission for.
