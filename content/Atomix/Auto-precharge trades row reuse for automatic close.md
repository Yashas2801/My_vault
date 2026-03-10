2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #auto_precharge

## Statement
Auto-precharge commands (RDA/WRA) close the row automatically after the burst finishes, saving an explicit PRE command.

## Why it matters
It is useful for workloads with low locality. However, it may hurt performance if the same row was likely to be reused soon.

## Mini visual
```text
Instead of: ACT -> RD -> PRE
Use:        ACT -> RDA (closes automatically after read)
```

## Links

* [[1.4 DDR Command Model]]
* [[PRE closes the row and equalizes the bitlines]]
* [[Row hit vs row miss in DDR]]
