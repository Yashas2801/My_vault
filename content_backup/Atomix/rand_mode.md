2025-03-07 16:47

Status: #done 

Tags: #constraints #constraint_methods
### rand_mode()
- **Purpose:** Controls the randomization behaviour for variables declared as `rand` or `randc`.
- It can disable or enable a randomization for a individual property or all the class properties
- **As a Task:**
    - Called with an argument (e.g., `pkt.data.rand_mode(0)`) to disable randomization for a specific variable.
    - Called with an argument on an object (e.g., `pkt.rand_mode(0)`) to disable randomization for all random variables in that object.
- **As a Function:**
    - When called without an argument (e.g., `pkt.data.rand_mode()`), it returns the current status of randomization (1 if enabled, 0 if disabled).
#### Example
```
class packet;
  rand bit [7:0] data;
  rand bit [7:0] addr;

  function void disp;
    $display("data = %0d, addr = %0d", this.data, this.addr);
  endfunction
endclass

module a;
  initial begin
    packet pkt = new;
    
    // Call 1
    pkt.randomize();
    pkt.disp;
    // Example Output: data = 42, addr = 137

    // Call 2
    if (pkt.data.rand_mode) begin
      pkt.data.rand_mode(0);
      pkt.randomize();
      pkt.disp;
      // Example Output: data = 42, addr = 55
    end

    // Call 3
    pkt.data.rand_mode(1);
    pkt.randomize();
    pkt.disp;
    // Example Output: data = 10, addr = 220

    // Call 4
    pkt.rand_mode(0);
    pkt.randomize();
    pkt.disp;
    // Example Output: data = 10, addr = 220
  end
endmodule

```
##### Explanation

**Call 1:**  
Both `data` and `addr` are randomized.  
_Example:_ `data = 42, addr = 137.`

**Call 2:**  
The `if` condition checks `pkt.data.rand_mode`, which is true (1) by default. Then `pkt.data.rand_mode(0)` disables randomization for `data`. On calling `pkt.randomize()`, only `addr` gets a new random value while `data` retains its previous value.  
_Example:_ `data = 42, addr = 55.`

**Call 3:**  
Randomization for `data` is re-enabled by calling `pkt.data.rand_mode(1)`. Now both variables are randomized again.  
_Example:_ `data = 10, addr = 220.`

**Call 4:**  
Finally, `pkt.rand_mode(0)` disables randomization for the entire object, so even though `pkt.randomize()` is called, none of the variables change.  
_Example:_ `data = 10, addr = 220` (same as Call 3).

---
**References (rand_mode)**
-	[Chatgbt](https://chatgpt.com/share/67c58eca-f5d0-800d-976d-9c5fbb693ecc)
- SV_BRN50 (Title name `oct 8 randomization`)
---