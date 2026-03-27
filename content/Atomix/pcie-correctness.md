---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #pcie #interface
---

# PCIe Correctness

**PCIe Correctness** ensures that the GPU SoC behaves as a compliant and reliable PCIe device when interacting with the host system.

### Verification Scope
- **Link Training & Enumeration**: Ensuring the link comes up at the correct speed and the host can discover the device.
- **Protocol Integrity**: TLP (Transaction Layer Packet) and DLLP (Data Link Layer Packet) correctness.
- **Configuration**: BAR (Base Address Register) sizing and MSI/MSI-X interrupt handling.
- **Data Transfer**: Inbound and outbound DMA (Direct Memory Access) reliability.
- **Error Handling**: Graceful recovery from PCIe-level errors.

> [!info] In Simple Words
> This checks whether the GPU behaves correctly as a PCIe device so the host can communicate with it reliably.

---

### Key Checkpoints
- [ ] SoC discovered correctly by host
- [ ] Correct packet exchange (TLP/DLLP)
- [ ] Reliable DMA transfers
- [ ] Proper interrupt generation
