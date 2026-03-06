2026-03-06 14:00
Status: #done
Tags: #ddr #vlsi #memory

# DDR SDRAM: A Comprehensive Overview

DDR (Double Data Rate) SDRAM is the backbone of modern computing memory. It was developed to address the growing performance gap between CPUs and memory, known as the **Memory Wall**.

## The Problem: The Memory Wall
As CPU frequencies scaled into the GHz range, the latency of main memory (DRAM) improved much more slowly. A typical CPU at 3GHz completes a cycle in ~0.33ns, while memory latency might be 60ns—meaning the CPU must wait for over 180 cycles for a single data request.

DDR focuses on improving **Bandwidth** (the volume of data moved per second) rather than **Latency** (the time to get the first bit).
- *See also:* [[Why DDR was created]], [[Blueprint Factory Analogy]]

---

## What is DDR?
**Double Data Rate Synchronous Dynamic Random Access Memory** (DDR SDRAM) differs from Single Data Rate (SDR) by transferring data on both the **rising and falling edges** of the clock signal. This effectively doubles the bandwidth for the same clock frequency.

| Feature | SDR | DDR |
| :--- | :--- | :--- |
| **Clock Edges** | Rising Only | Rising & Falling |
| **Transfers/Cycle** | 1 | 2 |
| **Power Efficiency**| Lower | Higher (same bandwidth at half freq) |

- *See also:* [[What is DDR?]], [[SDR vs DDR]]

---

## Underlying Technology: DRAM Cells
DDR is built on DRAM technology, which uses a simple **1-Transistor, 1-Capacitor (1T1C)** cell.
- **Dynamic**: The capacitor leaks charge and must be **refreshed** periodically (~64ms).
- **Density**: The simplicity of the cell allows for billions of bits per chip, making it much cheaper and denser than SRAM (used in caches).
- **Destructive Read**: Accessing a cell drains the capacitor's charge. The **Sense Amplifier** must detect this tiny change, amplify it, and **restore** the charge back to the cell.

- *See also:* [[DRAM Cell and Technology]], [[DRAM Refresh and Destructive Read]]

---

## Memory Architecture: The DRAM Array
Memory is organized into a 2D matrix of **Wordlines** (rows) and **Bitlines** (columns).

### The ACTIVATE Sequence
1. **Precharge**: Bitlines are set to a midpoint voltage.
2. **Activate**: A Wordline is pulled high, connecting capacitors to Bitlines (**Charge Sharing**).
3. **Sense & Amplify**: Sense amplifiers detect the voltage shift and latch the data into the **Row Buffer**.
4. **Restore**: The full logic levels are driven back into the capacitors.

- *See also:* [[The DRAM array]]

---

## Bandwidth and Generations
DDR has evolved through several generations, primarily by increasing the **Prefetch** (how many bits are fetched internally per external access) and reducing operating voltage.

### Evolution Table
| Gen | Typical Speed | Prefetch | Voltage |
| :--- | :--- | :--- | :--- |
| **DDR** | 200-400 MT/s | 2-bit | 2.5V |
| **DDR2** | 400-800 MT/s | 4-bit | 1.8V |
| **DDR3** | 800-1600 MT/s | 8-bit | 1.5V |
| **DDR4** | 1600-3200 MT/s | 8-bit+ | 1.2V |
| **DDR5** | 4800+ MT/s | 16-bit | 1.1V |

**Bandwidth Calculation**:  
$\text{Bandwidth (GB/s)} = \frac{\text{Transfer Rate (MT/s)} \times \text{Bus Width (bits)}}{8 \times 1000}$
(e.g., DDR4-3200 with 64-bit bus = 25.6 GB/s).

- *See also:* [[DDR Bandwidth and Generations]]
