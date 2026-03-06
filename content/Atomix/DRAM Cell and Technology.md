2026-03-05 17:30

Status: #done

Tags: #dram #cell

## DRAM Cell and Technology

DDR is built on **DRAM** (Dynamic Random Access Memory) technology, chosen for its high density.

## SRAM vs DRAM
| Memory Type | Storage Mechanism | Speed | Density | Typical Use |
| :--- | :--- | :--- | :--- | :--- |
| **SRAM** | Flip-flop (6T) | Very fast | Low | CPU Caches |
| **DRAM** | Capacitor (1T1C) | Slower | Very high | Main Memory (DDR) |

## The DRAM Cell (The Core of DDR)
Each DRAM cell consists of **1 Transistor** (for access) and **1 Capacitor** (for storage).

**Structure**:
```text
Bitline
  |
  T (Access Transistor)
  |
 Capacitor (Storage)
  |
 GND
```
Data is represented by the electrical charge in the capacitor:
- **Charged (High Voltage)**: Binary 1
- **Discharged (Low Voltage)**: Binary 0

Because of its extreme simplicity (only 2 components per cell), DRAM allows for billions of bits to be packed into a single chip.
