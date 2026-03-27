---
date: 2026-03-27 13:34
status: #done
tags: #dv #reset #power #clock #low-power #soc
---

# Reset, Power, and Clock

Modern SoCs do not operate in a single "always-on" state. This dimension verifies the transitions between various operational, idle, and power-saving states.

### Verification Scope
- **Multi-Clock Domain Stability**: Ensuring safe data transfer across asynchronous clock boundaries (CDC).
- **Idle & Gated States**: Entry and exit from low-power states without data loss or protocol violations.
- **Clean Resets**: Validating that all registers and state machines return to their reset values regardless of their previous state.
- **Power Sequencing**: Safe transitions during power-down and power-up sequences (if applicable).

> [!info] In Simple Words
> This dimension is basically: **“Do clock, reset, and power transitions happen safely?”**

---

### Key Verification Questions
- When a block is clock-gated (paused) and then resumes, was any internal state or data lost?
- Did synchronization between clock domains break during a frequency change?
- Does the design come back cleanly after a warm reset?

> [!example] Scenario: Block Pausing
> Suppose one block pauses to save power while another keeps running. When the paused block "wakes up," we must verify that the handshaking between them resumes correctly without dropping packets or causing a system hang.
