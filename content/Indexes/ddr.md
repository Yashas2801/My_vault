# DDR SDRAM Index

A comprehensive guide to DDR SDRAM technology, from physics and cell architecture to command protocols and system-level performance.

## 📚 Literature Notes (Synthesis)
Detailed overviews of core DDR concepts, organized in a clean learning flow.

- [[DDR fundamentals]] - The "Big Picture": Memory wall, SDR vs DDR, prefetch, and evolution.
- [[DRAM array and row buffer]] - Deep dive into bank organization, activation, and row buffer dynamics.
- [[DDR Command Model]] - The ACT -> RD/WR -> PRE lifecycle, bank interleaving, and configuration.
- [[DDR Timings and Performance]] - Synthesis of timing parameters, grouped by lifecycle stages.
- [[DDR Memory Hierarchy]] - The structural organization from Channel down to Column.
- [[C1 Interfaces around the DDR Controller]] - Boundary translation between SoC transactions and DDR protocols.

---

## 🔬 Atomic Notes (Core Concepts)

### 1. Fundamentals & Why DDR?
- [[Why DDR was created]]
- [[What is DDR?]]
- [[SDR vs DDR]]
- [[DDR Bandwidth and Generations]]
- [[Blueprint Factory Analogy]]

### 2. Physical Architecture & Hierarchy
- [[DDR memory hierarchy]]
- [[Rank]]
- [[Bank]]
- [[Row buffer]]
- [[Column access]]
- [[Burst length]]
- [[DRAM Cell and Technology]]
- [[DRAM Refresh and Destructive Read]]
- [[The DRAM array]]
- [[DDR - DRAM array hierarchy]]

### 3. Activation & Row Buffer
- [[DDR - ACT opens a row not a bit]]
- [[DDR - Row buffer and sense amplifiers]]
- [[DDR - Row address vs column address]]
- [[DDR - Row buffer size calculation]]
- [[DDR - Rank relation to row buffer]]
- [[DDR - Row hit vs row miss]]

### 4. Command Model & Lifecycle
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

### 5. Timings & Performance
- [[DDR-Timing-tRCD|tRCD - Row to Column Delay]]
- [[DDR-Timing-CL|CL - CAS Latency]]
- [[DDR-Timing-tRP|tRP - Row Precharge Time]]
- [[DDR-Timing-tRAS|tRAS - Row Active Time]]
- [[DDR-Timing-tRC|tRC - Row Cycle Time]]
- [[DDR-Timing-tRRD|tRRD - Row to Row Delay]]
- [[DDR-Timing-tFAW|tFAW - Four Activate Window]]
- [[DDR-Timing-tCCD|tCCD - Column to Column Delay]]
- [[DDR-Timing-tWTR|tWTR - Write to Read Delay]]
- [[DDR-Timing-tWR|tWR - Write Recovery Time]]
- [[DDR-Timing-tRTP|tRTP - Read to Precharge Delay]]
- [[DDR-Timing-tRFC|tRFC - Refresh Cycle Time]]

### 6. Memory Controller & Interfaces
- [[DDR controller sits between AXI interconnect and DDR PHY]]
- [[AXI side presents memory requests to the DDR controller]]
- [[DDR controller translates system transactions into DDR command flow]]
- [[DFI is the internal interface between DDR controller and DDR PHY]]
- [[Controller and PHY split protocol and physical responsibilities]]
- [[DDR PHY drives the external DDR4 SoDIMM interface]]
- [[DDR controller is programmed through configuration registers]]
- [[DDR controller depends on clock and reset sequencing]]
- [[DDR controller internally contains arbitration scheduling and command generation]]
- [[A read request travels AXI to controller to PHY to SoDIMM and back]]

---

## 📈 Roadmap Status
- **Fundamentals & Cell Basics** (#done)
- **DRAM Array & Row Buffer** (#done)
- **DDR Command Model** (#done)
- **Timings & Performance** (#done)
- **Memory Hierarchy** (#done)
- **Controller & Interfaces (C1)** (#done)
- **Next**: Internal Controller Pipeline (C2)
