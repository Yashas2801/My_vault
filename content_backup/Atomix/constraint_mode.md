2025-03-07 16:47

Status: #done 

Tags: #constraints #constraint_methods #sv
### Constraint_mode

- It is used to **enable** or **disable** a constraint.
```
pkt.data.constraint_mode(0)
```

- It can also disable all the constraints by
```
pkt.constraint_mode(0)
```

- It can also return a Boolean testing if the constraint is active or not
```
if (pkt.data.constraint_mode)
```

**`constraint_mode()` Method:**

- **As a Task:** When used with an argument, e.g., `pkt.data_c.constraint_mode(0)` or `pkt.constraint_mode(0)`, it disables or enables that specific constraint block or all the constraints respectively
- **As a Function:** When called without an argument, e.g., `pkt.data_c.constraint_mode()`, it returns the current status (1 for enabled, 0 for disabled).
#### Example 
```
class Packet;
  rand bit [7:0] data;
  rand bit [7:0] addr;
  constraint data_c { data inside {[10:20]}; }
  constraint addr_c { addr inside {100,150,200}; }
  
  function void disp();
    $display("data = %0d, addr = %0d", data, addr);
  endfunction
endclass

module tb;
  initial begin
    Packet pkt = new();

    // Call 1 
    pkt.randomize();
    pkt.disp();

    if (pkt.data_c.constraint_mode())
      $display("data_c is enabled");

    // Call 2
    pkt.data_c.constraint_mode(0);
    pkt.randomize();
    pkt.disp(); 

    if (!pkt.data_c.constraint_mode())
      $display("data_c is now disabled");

    // Call 3
    pkt.data_c.constraint_mode(1);
    pkt.randomize();
    pkt.disp();

    // Call 4
    pkt.constraint_mode(0);
    pkt.randomize();
    pkt.disp(); 
  end
endmodule

```

##### Explanation

**Call 1:**

- The object is randomized with both `data_c` and `addr_c` constraints active.
- The `disp()` function prints the constrained values for `data` (within 10 to 20) and `addr` (from the set {100, 150, 200}).

**Call 2:**

- The `data_c` constraint is disabled using `pkt.data_c.constraint_mode(0)`.
- Upon randomization, `data` becomes unconstrained (can be any 8-bit value), while `addr` remains within its constraint.
- The status of `data_c` is checked using its function form.

**Call 3:**

- The `data_c` constraint is re-enabled with `pkt.data_c.constraint_mode(1)`.
- Randomization now produces values for `data` that meet its constraint again, with `addr` remaining constrained.

**Call 4:**

- All constraints are disabled by calling `pkt.constraint_mode(0)`.
- When randomized, neither `data` nor `addr` is limited by any constraint.

---
**References (constraint_mode)**
-	[Grok](https://grok.com/share/bGVnYWN5_cef5c97e-e98a-4a30-b944-c93fe06b579c)
- SV_BRN50 (Title name `oct 8 randomization`)
---
