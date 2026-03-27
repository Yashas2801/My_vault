---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #axi #bus #protocol
---

# AXI Protocol Correctness

**AXI Protocol Correctness** verifies that all internal bus communications follow the strict rules of the AXI4 protocol.

### Core Requirements
Compliance must be checked on all major ports, including:
- **Handshaking**: Proper `VALID`/`READY` signal behavior.
- **Bursts**: Correct handling of incrementing and wrapping bursts.
- **Backpressure**: Ensuring the system handles stalls and congestion without data loss or deadlocks.
- **Transaction IDs**: Correct ordering and response matching for multiple outstanding transactions.

> [!info] In Simple Words
> Even if data reaches the right destination, the transfer is considered a failure if AXI protocol rules were violated along the way.

---

### Verification Checklist
- [ ] Valid/Ready handshake compliance
- [ ] Correct burst address calculation
- [ ] Proper response codes (OKAY, EXOKAY, SLVERR, DECERR)
- [ ] Deadlock-free backpressure handling
- [ ] Transaction ID ordering and matching
