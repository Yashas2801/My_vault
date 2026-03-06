2026-02-25 10:00

Status: #done

Tags: #systemverilog #polymorphism #sv_oop

### Polymorphism

Polymorphism allows a **base class handle** to invoke methods of an **extended class object** at runtime, provided the method is declared as `virtual`.

#### Code Example
```systemverilog
class base;
  virtual task send;
    $display("Base class method");
  endtask
endclass

class ext extends base;
  task send; // Overrides base::send
    $display("extended class method");
  endtask
endclass

module tb;
  base base_h;
  ext  ex_h = new;

  initial begin
    base_h = ex_h;   // Base handle points to Extended object
    base_h.send();   // Output: "extended class method"
  end
endmodule
```

---

### Mechanics: Compile Time vs. Run Time

| Phase           | Action                                                                                                                            |
| :-------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| **Compilation** | Compiler checks if `send()` exists in the **Handle Type** (`base`). Because it is `virtual`, it marks it for **Dynamic Binding**. |
| **Run Time**    | The simulator looks at the **Actual Object Type** the handle points to (`ext`) and executes that specific method.                 |

### Key Takeaways
- **Handle vs Object:** Method selection depends on the **Object type**, not the Handle type.
- **Virtual Requirement:** If `virtual` is omitted, the handle type (base) wins, and polymorphism is lost (Static Binding).
- **Binding:** Static binding happens at compile time; Dynamic binding happens at run time.

---

### UVM Relevance
- **Factory Overrides:** UVM uses polymorphism to substitute a base component with an extended one without modifying the source code.
- **Run Phases:** The UVM core calls `run_phase()` on `uvm_component` handles; polymorphism ensures your user-defined `run_phase` is the one that actually executes.
