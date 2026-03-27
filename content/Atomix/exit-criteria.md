---
date: 2026-03-27 13:34
status: #done
tags: #dv #coverage #exit-criteria #sign-off
---

# Exit Criteria

**Exit Criteria** define the "Definition of Done" for the verification phase. It provides the measurable proof required to sign off on the SoC's verification status.

### The Completion Checklist
SoC Design Verification (DV) is considered complete only when the following targets are met:

- [ ] **Functional Coverage**: Target functional coverage bins are at **100%**.
- [ ] **Code/Toggle Coverage**: At least **95%** coverage on important SoC areas (Statement, Branch, Condition, Toggle).
- [ ] **Regression Pass Rate**: All tests in the regression suite must be at a **100% pass rate**.

> [!info] In Simple Words
> This tells the team when they are allowed to say: **“Verification is complete enough to sign off this stage.”**

---

### Why Measurable Proof Matters
It is not enough to say "we ran some tests" or "things looked okay." Exit criteria ensure:
1. **Enough Scenarios**: Every important functional situation was exercised.
2. **Enough Activity**: The RTL code was thoroughly toggled and stimulated.
3. **Stability**: The entire suite is consistently passing without random failures.

> [!tip] Interpretation
> Exit criteria act as the **final quality gate** before the design moves to the next stage of the lifecycle.
