## TLM Basics [[UVM TLM Basics]]

A foundational overview of UVM TLM communication and port binding mechanics.

**Topics Covered:**
- What is TLM
- Types of Ports in TLM
- Working of TLM
- TLM Directional Summary

## Full Port List
See [[UVM TLM Port List]] for a complete matrix of Port, Export, and Imp types.

## TLM Methods
TLM methods are categorized into **Blocking** (waits for success) and **Non-blocking** (returns immediately with status). 
- **Blocking**: `put()`, `get()`, `peek()`
- **Non-blocking**: `try_*`, `can_*` and `write()` (Analysis).

See [[uvm tlm methods]] for a full breakdown of each method's behavior and usage.
