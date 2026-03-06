2025-03-07 16:47

Status: #done 

Tags: #constraints #types_of_constraints

## Set Membership
**Keyword Used**: `inside`
### What is it?
- It restricts a property's value to a set of values. The set can also include ranges and arrays.
**Usage**
```systemverilog
constraint constraint_identifier{
	property inside{set of leagl values};
}
```
**Example**
```systemverilog
rand bit[7:0]data;
constraint c1{data inside {2,3,5, [12:35]}; }
```


### References 

- SV_BRN50 (Title name `oct 8 randomization`)

