# DDR SDRAM Index

A comprehensive guide to DDR SDRAM technology, from physics and cell architecture to command protocols and system-level performance.

## 📚 Literature Notes (Synthesis)
Detailed overviews of core DDR concepts, organized by study stages.

- [[DDR fundamentals]] - The "Big Picture": Memory wall, SDR vs DDR, prefetch, and evolution.
- [[Stage 1.3 - DRAM array and row buffer]] - Deep dive into bank organization, activation, and row buffer dynamics.
- [[1.4 DDR Command Model]] - The ACT -> RD/WR -> PRE lifecycle, bank interleaving, and configuration.

---

## 🔬 Atomic Notes (Core Concepts)

### 1. Fundamentals & Why DDR?
- [[Why DDR was created]]
- [[What is DDR?]]
- [[SDR vs DDR]]
- [[DDR Bandwidth and Generations]]
- [[Blueprint Factory Analogy]]

### 2. DRAM Cell & Array Physics
- [[DRAM Cell and Technology]]
- [[DRAM Refresh and Destructive Read]]
- [[The DRAM array]]
- [[DDR - DRAM array hierarchy]]

### 3. Activation & Row Buffer (Stage 1.3)
- [[DDR - ACT opens a row not a bit]]
- [[DDR - Row buffer and sense amplifiers]]
- [[DDR - Row address vs column address]]
- [[DDR - Row buffer size calculation]]
- [[DDR - Rank relation to row buffer]]
- [[DDR - Row hit vs row miss]]

### 4. Command Model & Lifecycle (Stage 1.4)
- [[DDR Commands]]
- [[ACT opens a row into the row buffer]]
- [[RD reads columns from an already open row]]
- [[WR writes through the active row buffer path]]
- [[PRE closes the row and equalizes the bitlines]]
- [[PRE does not erase column data]]
- [[Row hit vs row miss in DDR]]
- [[Auto-precharge trades row reuse for automatic close]]
- [[REFRESH is mandatory because DRAM cells leak]]
- [[MRS configures DRAM behavior]]
- [[Bank interleaving improves DDR throughput]]

---

## 📈 Roadmap Status
- **Stage 1.1 - 1.2**: Fundamentals & Cell Basics (#done)
- **Stage 1.3**: DRAM Array & Row Buffer (#done)
- **Stage 1.4**: DDR Command Model (#done)
- **Stage 1.5**: Next (Timings, Scheduling, etc.)
