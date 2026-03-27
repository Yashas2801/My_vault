---
date: 2026-03-27 13:34
status: #done
tags: #dv #staging #roadmap #soc
---

# Staging Plan

A **staging plan** serves as a roadmap for the Design Verification (DV) team, defining what to build first, what comes next, and what will be integrated later.

### Why It Matters
A full SoC testbench is too complex to build all at once. Staging ensures a systematic, phased build of the DV environment.

> [!info] In Simple Words
> It is the **roadmap** for constructing the DV environment in phases.

---

### Phase-by-Phase Roadmap

#### **Stage 1: Basic TB Bring-up**
- [ ] Basic TB architecture established
- [ ] Clocks and reset logic working
- [ ] DUT instantiation
- [ ] Simple sanity tests running

#### **Stage 2: Interface Connectivity**
- [ ] PCIe VIP connected
- [ ] DDR model integrated
- [ ] Basic host programming functional
- [ ] Simple traffic flows enabled

#### **Stage 3: Feature Completeness**
- [ ] Kernel launch flow functional
- [ ] Scoreboards and checkers added
- [ ] Basic regressions enabled

#### **Stage 4: Verification Closure**
- [ ] Robustness and error injection tests
- [ ] Full functional and code coverage achieved
- [ ] Gate Level Simulation (GLS) bring-up
