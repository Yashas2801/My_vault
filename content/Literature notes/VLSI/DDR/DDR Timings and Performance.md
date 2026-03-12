# DDR Timings and Performance

DDR memory is governed by a strict set of timing parameters. These timings ensure that the physical analog operations (like sensing charge, precharging bitlines, and restoring data) complete safely before the next logical operation begins. 

Timings are logically grouped into families based on the memory lifecycle stage they protect.

## 1. Row Activation (Opening the Row)
Before reading or writing, a row must be activated and the data must stabilize in the sense amplifiers (Row Buffer).
- **[[DDR-Timing-tRCD|tRCD (Row to Column Delay)]]**: The time required to sense and amplify the cell charge. The controller must wait this long after `ACT` before issuing a `RD` or `WR` command.
- **[[DDR-Timing-tRAS|tRAS (Row Active Time)]]**: The minimum time a row must remain open. It ensures the sense amplifiers have enough time to fully restore the destructive read charge back into the DRAM cells.

## 2. Row Precharge and Closing
To access a different row in the *same bank*, the currently open row must be closed and the bitlines precharged back to a neutral state.
- **[[DDR-Timing-tRP|tRP (Row Precharge Time)]]**: The time it takes to close a row and precharge the bank. You must wait this long after `PRE` before issuing the next `ACT` to that same bank.
- **[[DDR-Timing-tRC|tRC (Row Cycle Time)]]**: The total minimum cycle time for a single bank (`tRAS + tRP`). It dictates the absolute fastest rate you can open, close, and re-open rows in the same bank.
- **[[DDR-Timing-tWR|tWR (Write Recovery Time)]]**: Protects the cell write-back process. You must wait `tWR` after a `WR` burst finishes before you can safely issue a `PRE` to close the row.
- **[[DDR-Timing-tRTP|tRTP (Read to Precharge Delay)]]**: Ensures the internal read burst completes safely before the bank is precharged via `PRE`.

## 3. Column Accesses (Reading and Writing)
Once a row is safely open, data is moved through the internal column and I/O pipelines.
- **[[DDR-Timing-CL|CL (CAS Latency)]]**: The time between issuing a `RD` command and receiving the first piece of valid data on the data bus.
- **[[DDR-Timing-tCCD|tCCD (Column to Column Delay)]]**: The minimum spacing between consecutive column commands (e.g., `RD` to `RD`, or `WR` to `WR`) to prevent pipeline collisions.
- **[[DDR-Timing-tWTR|tWTR (Write to Read Delay)]]**: The bus turnaround time. The time required to switch the internal data paths and external bus from driving data in (write) to driving data out (read).

## 4. Multi-Bank & Power Constraints
Row activation (`ACT`) consumes a substantial surge of power. To prevent voltage drops or power delivery network (PDN) collapse, the DRAM limits how densely activations can be packed across the entire chip.
- **[[DDR-Timing-tRRD|tRRD (Row to Row Delay)]]**: The minimum spacing between `ACT` commands to *different* banks.
- **[[DDR-Timing-tFAW|tFAW (Four Activate Window)]]**: A rolling window that restricts the system to no more than four `ACT` commands within a specific timeframe, preventing clustered power spikes.

## 5. Maintenance
- **[[DDR-Timing-tRFC|tRFC (Refresh Cycle Time)]]**: The time the DRAM array remains completely busy during a `REF` (Refresh) command. No other access commands can be issued until this background process completes.

---
**Related Indexes & Notes:**
- [[Indexes/ddr|DDR Index]]
- [[DDR Commands]]
