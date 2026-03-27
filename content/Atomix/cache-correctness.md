---
date: 2026-03-27 13:34
status: #done
tags: #dv #correctness #cache #memory
---

# Cache Correctness

**Cache Correctness** verifies that the hierarchical memory system (L1 Instruction/Data, L2 Shared Cache) returns the correct data and manages its state properly.

### Core Requirements
The system must behave correctly across all cache operations:
- **Hits**: Returning the correct data immediately.
- **Misses**: Fetching the correct data from the next level of memory.
- **Evictions**: Ensuring dirty data is written back correctly to maintain consistency.
- **Policies**: Proper implementation of write-through or write-back policies.

> [!info] In Simple Words
> If data was updated in one place, the cache must not return "stale" (old) data by mistake.

---

> [!example] Cache Scenarios
> - **Hit**: Does it return the data without going to DDR?
> - **Miss**: Does it stall correctly and fetch from L2/DDR?
> - **Eviction**: When a line is replaced, is the old data safely saved?
