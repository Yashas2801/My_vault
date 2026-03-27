---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #ddr #memory
---

# DDR Correctness

**DDR Correctness** focuses on the interface between the SoC and external DDR4 memory, ensuring that data is stored and retrieved reliably according to protocol timings.

### Core Requirements
- **Protocol Compliance**: Adherence to DDR4 timing and handshake abstractions at the controller/PHY interface.
- **Initialization**: Proper memory initialization and training sequences.
- **Data Integrity**: Correct read/write ordering, refresh impact management, and ECC (Error Correction Code) behavior if implemented.

> [!info] In Simple Words
> The GPU might compute the right result, but if the DDR interface is buggy, the final data stored in memory will be wrong.

---

### Key Verification Areas
- **Timing Compliance**: Meeting strict JEDEC requirements.
- **Read/Write Ordering**: Ensuring data consistency across multiple requests.
- **Refresh Operations**: Verifying that periodic refreshes don't corrupt active data or cause excessive stalls.
- **ECC**: Validating that single-bit errors are corrected and multi-bit errors are detected.
