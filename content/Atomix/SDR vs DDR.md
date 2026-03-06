2026-03-05 17:30

Status: #done

Tags: #ddr #sdr

## Single Data Rate vs Double Data Rate

## Single Data Rate (SDR)
Data transfers once per clock cycle, typically on the rising edge.

- **Clock**:  ↑    ↑    ↑    ↑
- **Data**:  D1   D2   D3   D4
- **Transfers per cycle**: 1

## Double Data Rate (DDR)
Data transfers on both the **rising edge** and the **falling edge** of the clock.

- **Clock**:  ↑    ↓    ↑    ↓
- **Data**:  D1   D2   D3   D4
- **Transfers per cycle**: 2

**Key Benefit**: Bandwidth doubles without requiring a doubling of the clock frequency, which helps manage power consumption and signal integrity.
