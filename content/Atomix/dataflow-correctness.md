---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #dataflow #gpu
---

# End-to-End Dataflow Correctness

**End-to-end dataflow** verification ensures that data moves correctly from its original source to its final destination across the entire SoC, rather than just across isolated interfaces.

### Major Data Paths
The verification strategy identifies three primary paths that must be validated:
1. **GPU Compute Path**: 
   `4 SPs → AXI Crossbar → L1 TLBs/Caches → NIC → L2 → NCCI → DDR/PCIe`
2. **Host-to-GPU Path**: 
   `Host RC → PCIe PHY → PCIe Controller → NCCI → L2/DDR`
3. **GPU-to-Host Path**: 
   `Compute Pipeline → L2 → NCCI → PCIe Controller → PCIe PHY → Host`

> [!info] In Simple Words
> We must prove that data goes correctly from start to finish. It's about the **whole route**, not just one interface working alone.

---

### Key Verification Questions
- Did the data enter the system correctly?
- Did it traverse the intended internal path without corruption?
- Did memory behavior (ordering, consistency) stay correct?
- Did the final result reach the destination as expected?

> [!tip] Concept
> “End-to-end” means **full path integrity**, ensuring that the integration of blocks doesn't introduce data loss or corruption.
