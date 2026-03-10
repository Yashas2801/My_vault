2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #architecture #performance

## Statement
While one bank waits for an activation or precharge delay, another bank can serve data.

## Why it matters
Overlapping operations across different banks hides the inherent timing delays (like tRCD or tRP) and dramatically improves overall memory throughput.

## Mini visual
```text
Bank 0: ACT ---- wait ---- RD ---- PRE
Bank 1:      ACT ---- wait ---- RD ---- PRE
```

## Links

* [[1.4 DDR Command Model]]
