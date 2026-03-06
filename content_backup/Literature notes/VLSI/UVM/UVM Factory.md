### What is UVM Factory?
- It is a special look up table.
- It uses the 'create' method to create the objects.
- The create method implicitly calls the constructor which has different template based on weather it is a component or a object

### Template of COMPONENT type
```systemverilog
function new(string name, uvm_component parent);
	super.new(name,parent);	
endfunction
```
- When we use the create method, we pass *this* as a second argument.
- The leaf level component will be aware of who is its parent and know the level of the hierarchy.
### Template of OBJECT type
```systemVerilog
function new(string name = "class_name");
	super.new(name);
endfunction
```
- There are times when handles for *objects* are created so it is most recommended to give the default name i.e *class_name*.
### Create Method syntax
```systemVerilog
handle_name = class_name::type_id::create(handle_name,this)
``` 
- The factory create method is used to create objects in UVM.
- function *new* is implicitly called to create an object (More about function *new* ,refer [[oops basics]])

### Factory Overriding
- There are 2 types of factory overriding
	- #### Type override by type/name
	- #### Instance override by type/name

