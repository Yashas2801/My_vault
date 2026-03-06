2026-03-05 17:30

Status: #done

Tags: #ddr

## Why DDR was created

- The main problem which was to be addressed was the **Memory Wall**

## What is Memory Wall
- This is the growing gap between of the **CPU speed** and **Memory access speed**
- Over time, CPU speed increased rapidly but the Memory latency improved very slowly
- **The scale**
	- CPUs improved 1000x
	- Memories improves ~4x
### Example: The Performance Gap
- **CPU Specifications**: 3 GHz Frequency $\rightarrow$ **0.33 ns** per clock cycle.
- **Memory Specifications**: **60 ns** Latency for a single data request.
- **The Calculation**:
    - $\text{Wait Cycles} = \frac{\text{Memory Latency}}{\text{CPU Clock Period}} = \frac{60\text{ ns}}{0.33\text{ ns}} \approx \mathbf{181 \text{ cycles}}$
- **The Result**: The CPU must sit idle for over **180 cycles** for every data request, illustrating the massive bottleneck that DDR technology helps bridge.

## Important Concept: Bandwidth vs Latency

**DDR mostly improves bandwidth, not latency.**

While DDR technology has advanced through many generations (DDR2, DDR3, DDR4, DDR5), the fundamental way it improves performance is by increasing the **volume** of data it can move, rather than the **speed** of the initial request.

### Basic Comparison

| Metric        | Meaning                                | DDR Impact                                                  |
| :------------ | :------------------------------------- | :---------------------------------------------------------- |
| **Latency**   | Time to get the **first** bit of data. | **Small improvement** (remains ~10-15ns for decades).       |
| **Bandwidth** | Amount of data moved **per second**.   | **Significant increase** (doubles almost every generation). |

---

For a simpler analogy, see the [[Blueprint Factory Analogy]].