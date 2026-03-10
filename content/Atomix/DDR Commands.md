2026-03-08 20:24

Status: #done  

Tags: #SoDIMM #rank #ddr #commands

Pre-requisites: [[The DRAM array]]

DDR Commands are sent from `DDR controller` to the external `SoDIMM`
where all the DRAM chips via `DDR PHY`

## ACT (Activate) Command 
- Bank is chosen
- Row is chosen
- The row's wordline turns on
- All the capacitors of that row are connected to their respective bitline
- The capacitors discharge to their respective bitline
- This change is sensed and amplified by sense amplifiers
- The value of the row is copied to raw buffer

## RD (Read) Command
- A specific column address is chosen.
- The command accesses the data already present in the currently active row buffer (sense amplifiers).
- Data starting from the selected column is routed to the external data bus.
- Data is transferred out in a continuous burst (e.g., 8 data beats).
- **Note:** RD does not open a row; it requires a row to be active already.

## WR (Write) Command
- A specific column address is chosen.
- The command targets the currently active row buffer.
- Incoming data bursts from the external data bus are routed to the sense amplifiers.
- The data is written into the open row buffer starting at the selected column.
- **Note:** Like RD, WR requires a row to be active and does not open a row itself.

## PRE (Precharge) Command
- The currently active row in the selected bank is closed.
- The wordline for the active row is turned off, disconnecting the cell capacitors from the bitlines.
- Data in the row buffer is driven back to fully restore the charge in the DRAM cells (closing the row).
- The bitlines are precharged back to their intermediate reference voltage (e.g., VDD/2).
- The bank returns to an idle state, making it ready for a new ACT command.

## REFRESH Command
- A maintenance command required because DRAM cell capacitors leak charge over time.
- Normal data accesses to the memory are temporarily paused.
- Internal DRAM counters automatically select the next rows to be refreshed.
- Selected rows are internally activated (charge sensed and restored) and then precharged.

## MRS (Mode Register Set) Command
- A configuration command used primarily during memory bring-up and initialization.
- Programs the internal DRAM mode registers.
- Sets critical operational parameters like CAS Latency (CL), Burst Length (BL), and ODT (On-Die Termination).
- Does not access or move user data.

### References 
- [SystemVerilog.io DDR4 Basics](https://www.systemverilog.io/design/ddr4-basics/)