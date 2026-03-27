---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #mmu #tlb #translation
---

# Translation Correctness

**Translation Correctness** verifies that the Memory Management Unit (MMU) and Translation Lookaside Buffer (TLB) correctly map virtual addresses to physical addresses and enforce security permissions.

### Core Requirements
Verification covers the L2-side MMU/TLB functionality:
- **VA → PA Mapping**: Ensuring the Virtual Address maps to the intended Physical Address.
- **Permissions**: Enforcing read/write/execute protections.
- **Page Sizes**: Handling different page granularities correctly.
- **Invalidation (TLBI)**: Ensuring stale translations are removed when the software requests a flush.

> [!info] In Simple Words
> When software asks for data at Address X, this logic ensures the hardware looks in the right physical spot and checks if the software is actually allowed to see it.

---

### Key Scenarios
- [ ] Successful VA to PA translation
- [ ] Permission fault generation on illegal access
- [ ] Correct behavior after TLB invalidation
- [ ] Multi-page size support
