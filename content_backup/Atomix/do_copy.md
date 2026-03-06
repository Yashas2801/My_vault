2025-03-13 18:04

Status: #to_be_done

Tags: #uvm_factory #do_hooks


**What is does**
- performs deep_copy of an object.

**code example:**
```systemverilog
function void do_copy(uvm_object rhs);
	write_xtn rhs_;
	assert($cast(rhs_,rhs));
	else `uvm_fatal(get_type_name,"Failed to assign child to parent")
	super.do_copy(rhs);
	this.data = rhs_.data;
	this.addr = rhs_.addr;
endfunction
```

The `do_copy` method is a virtual function in UVM used to perform a deep copy of an object’s data members from a source object (`rhs`) to the current object (`this`).

when a object is passed , for example
```systemverilog
write_xtn xtn1,xtn2;
//Assume xtn1 values are assigned and we are trying to copy contents of xtn1 to xtn2
xtn2.copy(xtn1);
```
The following happens internally.
`rhs = xtn1` 

### References 



