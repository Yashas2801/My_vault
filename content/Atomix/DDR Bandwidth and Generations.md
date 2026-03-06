2026-03-05 17:30

Status: #done

Tags: #ddr #bandwidth

## DDR Bandwidth and Generations

DDR performance is characterized by how much data it can transfer per second.

## DDR Bandwidth Calculation
For a **DDR4-3200** memory module:
- **Speed**: 3200 Million Transfers per second (MT/s).
- **Bus Width**: 64 bits (standard for a single 64-bit memory channel).

**The Calculation**:
- $3200 \times 64 \text{ bits} = 204,800 \text{ Megabits per second (Mb/s)}$
- $204,800 / 8 = \mathbf{25.6 \text{ Gigabytes per second (GB/s)}}$

This bandwidth can be further increased by using **Dual-Channel** (128-bit bus) or **Quad-Channel** (256-bit bus) memory configurations.

## Evolution of DDR Generations

| Generation | Typical Speed    | Key Improvements                          |
| :--------- | :--------------- | :---------------------------------------- |
| **DDR**    | 266 - 400 MT/s   | 2-bit prefetch, 2.5V operation            |
| **DDR2**   | 400 - 800 MT/s   | 4-bit prefetch, 1.8V operation            |
| **DDR3**   | 800 - 1600 MT/s  | 8-bit prefetch, 1.5V operation            |
| **DDR4**   | 1600 - 3200 MT/s | Bank groups, 1.2V operation               |
| **DDR5**   | 4800+ MT/s       | Dual 32-bit subchannels, 1.1V, On-die ECC |

Each successive generation increases bandwidth while reducing voltage and power consumption.
