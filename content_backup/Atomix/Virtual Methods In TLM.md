2026-02-25 10:00

Status: #done

Tags: #sv_oop #uvm #tlm

When implementing TLM methods (like `put`, `get`, `peek`) in a target component, it is standard practice to declare them as `virtual`.

## Why use `virtual`?

### 1. Polymorphism and Inheritance
Declaring a method as `virtual` allows it to be **overridden** in child classes. If you extend a base consumer component to create a more specialized version, making the `put()` task `virtual` ensures that the TLM port calls the **new** implementation in the child class, not the old one in the base class.

### 2. Run-time Binding
In SystemVerilog, `virtual` enables **dynamic binding**. This means the method call is resolved at run-time based on the actual object type, rather than at compile-time based on the handle type. This is crucial for UVM's modular architecture.

### 3. Extensibility
Making methods `virtual` makes your components "future-proof." Other engineers can extend your components and change their TLM behavior without needing to modify your original source code.

## Example
```systemverilog
class my_consumer extends uvm_component;
  `uvm_component_utils(my_consumer)
  uvm_blocking_put_imp#(my_transaction, my_consumer) put_imp;

  function new(string name, uvm_component parent);
    super.new(name, parent);
    put_imp = new("put_imp", this);
  endfunction

  // Declaring as virtual to allow for future overriding
  virtual task put(my_transaction t);
    `uvm_info("CONS", "Transaction received", UVM_LOW)
    // Process transaction...
  endtask
class my_consumer extends uvm_component;
  `uvm_component_utils(my_consumer)
  uvm_blocking_put_imp#(my_transaction, my_consumer) put_imp;

  function new(string name, uvm_component parent);
    super.new(name, parent);
    put_imp = new("put_imp", this);
  endfunction

  // Declaring as virtual to allow for future overriding
  virtual task put(my_transaction t);
    `uvm_info("CONS", "Transaction received", UVM_LOW)
    // Process transaction...
  endtask
endclass
```
