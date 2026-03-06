2026-02-25 10:00

Status: #done

Tags: #uvm #tlm
## What is TLM
- Transaction level modelling is used to establish communication among TB components.
- It supports *interoperability* (Different components written in different languages can communicate using TLM ports)

## Types of Ports in TLM

| Port Type                | Description                                                                                                                    |
| :----------------------- | :----------------------------------------------------------------------------------------------------------------------------- |
| **Port**                 | The _initiator_ component always has _port_ ,that calls methods (like `put`, `get`) to communicate.                            |
| **Export**               | A component that promotes or forwards an implementation to an upper level.                                                     |
| **Implementation (Imp)** | The _Target_ component always has _Imp_port_ that actually contains the implementation of the TLM methods (like `put`, `get`). |
| **Analysis Port**        | Used for broadcasting transactions to one or more subscribers (observers).                                                     |

## Working of TLM

TLM communication is established through a specific relationship between two components:

1.  **Initiator vs. Target**:
    *   **Initiator**: The component that starts the communication by calling a TLM method (e.g., `put()`, `get()`).
    *   **Target**: The component that responds to the call and contains the logic.

2.  **The Binding Mechanism**:
    *   The **Initiator** contains a **Port**.
    *   The **Target** contains an **Implementation Port (Imp)**.
    *   In the `connect_phase`, they are bound together: `producer.port.connect(consumer.imp_port)`.

3.  **Key Implementation Rules**:
    *   **Explicit Implementation**: The user must explicitly define the method logic (e.g., `task put(xtn xtn_h)`) within the target component. 
    *   **Virtual Methods**: These methods should be declared as `virtual` to ensure polymorphism and extensibility. For a detailed explanation, see [[Virtual Methods In TLM]].




## TLM Directional Summary

| Scenario | Initiator (Port)                                            | Target (Implementation)                                       | Action Flow                                              |
| :------- | :---------------------------------------------------------- | :------------------------------------------------------------ | :------------------------------------------------------- |
| **Push** | **Source** (Initiator)<br>`uvm_blocking_put_port #(T)`      | **Destination** (Target)<br>`uvm_blocking_put_imp #(T, Dest)` | Calls `port.put(t)`<br>$\to$ Defines `task put(T t)`     |
| **Pull** | **Destination** (Initiator)<br>`uvm_blocking_get_port #(T)` | **Source** (Target)<br>`uvm_blocking_get_imp #(T, Src)`       | Calls `port.get(t)`<br>$\to$ Defines `task get(out T t)` |
