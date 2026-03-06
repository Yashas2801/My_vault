2026-02-25 10:00

Status: #done

Tags: #uvm #tlm

This table summarizes the available UVM TLM classes for Port, Export, and Implementation (Imp) across different operation modes.

[[Literature notes/Zettelkasten]]### UVM TLM Port/Export/Imp Matrix

| Type       | Mode         | Put (Push)                   | Get (Pull)                   | Peek (Observe)                |
| :--------- | :----------- | :--------------------------- | :--------------------------- | :---------------------------- |
| **Port**   | Blocking     | `uvm_blocking_put_port`      | `uvm_blocking_get_port`      | `uvm_blocking_peek_port`      |
|            | Non-blocking | `uvm_nonblocking_put_port`   | `uvm_nonblocking_get_port`   | `uvm_nonblocking_peek_port`   |
|            | Combined     | `uvm_put_port`               | `uvm_get_port`               | `uvm_peek_port`               |
| **Export** | Blocking     | `uvm_blocking_put_export`    | `uvm_blocking_get_export`    | `uvm_blocking_peek_export`    |
|            | Non-blocking | `uvm_nonblocking_put_export` | `uvm_nonblocking_get_export` | `uvm_nonblocking_peek_export` |
|            | Combined     | `uvm_put_export`             | `uvm_get_export`             | `uvm_peek_export`             |
| **Imp**    | Blocking     | `uvm_blocking_put_imp`       | `uvm_blocking_get_imp`       | `uvm_blocking_peek_imp`       |
|            | Non-blocking | `uvm_nonblocking_put_imp`    | `uvm_nonblocking_get_imp`    | `uvm_nonblocking_peek_imp`    |
|            | Combined     | `uvm_put_imp`                | `uvm_get_imp`                | `uvm_peek_imp`                |
