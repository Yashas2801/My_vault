2026-03-10 17:30

Status: #done

Tags: #ddr #vlsi #memory #commands #precharge

## Statement
PRE resets the access state of the bank only. There is no user data erasure. Columns are access positions, not a separate memory that gets cleared.

## Why it matters
Clears up the confusion that "closing" a row or precharging "resets" the actual data stored in the memory cells.

## Links

* [[DDR Command Model]]
* [[PRE closes the row and equalizes the bitlines]]
