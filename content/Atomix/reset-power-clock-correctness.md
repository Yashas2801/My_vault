---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #reset #power #clock
---

# Reset, Clock, and Power Correctness

This dimension of correctness ensures that the SoC remains stable and functional during intentional transitions in its operating state.

### Core Requirements
- **Clean Resets**: Ensuring the system returns to a known-good state after a reset signal.
- **Power Sequencing**: Safe transitions during power-up and power-down sequences.
- **Clock Stability**: Ensuring clocks are stable and at the correct frequency before internal blocks begin operation.

> [!info] In Simple Words
> Even in normal, intended use, resets and state transitions should not break the system or leave it in an undefined state.

---

### Verification Focus
- **Power-on Reset (POR)**: Validating the initial cold-boot sequence.
- **Warm Resets**: Checking system recovery without a full power cycle.
- **Dynamic Clock/Power Gates**: Verifying that turning off sub-blocks for power saving doesn't corrupt the rest of the system.
