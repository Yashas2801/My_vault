---
date: 2026-03-27 13:34
status: #done
tags: #dv #verification #strategy #soc
---

# Verification Strategy

### What is Verification strategy:
- Gives the overall context of the Verification of the SOC
- What is being verified
- What is not being verified
- How [[Kernal]] request goes from host to GPU
- What are the the IP's we have
- Do we need to verify the IP's


### Intro:
- We are doing SOC level verification
- All the IP's are assumed to be verified
- *Our Job:* To verify if all the blocks are working properly when the host dumps the work on it.

#### What is GPU
- It is a specialized general purpose hardware.
- Built to accelerate compute heave tasks like matrix multiplication, [[tensor]] operations etc 

### Scope of Verification
- Defining verification strategy and TB architecture.
- Create [[test-plan]], [[coverage-plan]] and [[staging-plan]]
- developing the testbench with VIPs and RAL
- [[creating-kernels]], [[compiling-kernels]], [[driving-kernels]], and [[launching-kernels]] from the host [[kernel-launch-flow]]
- SoC-level verification with checkers and testcases
- regression and coverage analysis
- GLS ZD and SDF simulations

*It excludes:*
- benchmarking and performance validation
- simulations using actual boot code
- multi-die simulations
- host software co-simulation

### Dimensions of verification

>What exactly do we need to prove at SoC level?

> [!info] In Simple Words
> **Dimensions of verification means the different angles from which the full GPU SoC must be verified before we call it done**

The verification effort is categorized into several key dimensions, each focusing on a different aspect of system integrity:

> [!shield] [[correctness|Correctness]]
> Verifies if the SoC works properly under normal conditions and meets all functional specifications.

> [!shield] [[robustness-ras|Robustness & RAS]]
> Ensures the system behaves safely and predictably in abnormal conditions, including error handling and reliability features.

> [!power] [[reset-power-clock|Reset/Power/Clock]]
> Validates that resets, clocks, and power-related transitions behave cleanly and follow the expected sequencing.

> [!flag] [[exit-criteria|Exit Criteria]]
> Defines the specific metrics and milestones (e.g., coverage targets, bug rates) that must be met to consider verification complete.

**Formal Connectivity**
> Utilizes formal methods to check internal and external connections (Note: Specific checks are still TBD).
