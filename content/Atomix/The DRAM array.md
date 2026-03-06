2026-03-05 17:30

Status: #done

Tags: #dram #architecture

## The DRAM Array

- A DRAM cell consists of a capacitor and a transistor



---

## 2D DRAM Cell Matrix

Each cell sits at the intersection of a **wordline** and **bitline**.

```
                        C1         C2         C3         C4
                     Bitline0   Bitline1   Bitline2   Bitline3
                        |          |          |          |
                        |          |          |          |
R1  Wordline0  ----   [C]T       [C]T       [C]T       [C]T
R2  Wordline1  ----   [C]T       [C]T       [C]T       [C]T
R3  Wordline2  ----   [C]T       [C]T       [C]T       [C]T
R4  Wordline3  ----   [C]T       [C]T       [C]T       [C]T

                       SA         SA         SA         SA
                        |          |          |          |
               +------------------------------------------+
               |                Row Buffer                |
               +------------------------------------------+
```

Where:

- Horizontal lines = **Wordlines**
- Vertical lines = **Bitlines**
- Each `[C]T` = one **DRAM cell (1 transistor + 1 capacitor)**
- `SA` = Sense amplifier
- **Row Buffer** = Temporary latch that holds the data of the currently activated row.

---

### Sequence of Operation (ACTIVATE)

1. **Precharge State**: Bitlines are precharged to $V_{DD}/2$.
2. **ACTIVATE**: The wordline goes high, turning on the access transistors and connecting all cell capacitors in that row to their bitlines. **Charge sharing** occurs.
3. **Sense Amplification**: The small voltage difference created on the bitlines ($V_{DD}/2 + \Delta V \rightarrow 1$ or $V_{DD}/2 - \Delta V \rightarrow 0$) is detected and amplified by sense amplifiers to full logic levels.
4. **Row Buffer Formation**: The sense amplifiers latch the data and hold the entire row, forming the **Row Buffer**.
5. **Restore**: This process is known as a **Destructive Read** because the charge sharing operation disturbs the stored charge in the cell capacitor. To maintain data integrity, the sense amplifiers must restore the full voltage levels back into the capacitors.















