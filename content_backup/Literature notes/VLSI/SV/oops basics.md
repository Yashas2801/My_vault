**Basic terminologies**
`class` `object` `new()` `handle`

**class** - a class is a like a blueprint that encapsulates methods and properties into a single package. A class is used to create a object.
	example `class packet`

**handle/address** - it holds the address of the object and acts as a pointer to the object.
	example `packet p1,p2;`

**object** - an object is a instance of a class.
	example `p1 = new()`

**default Constructor/new()** - new is a builtin function(constructor) that is used to create objects from a class.
	It does 3 main things,
		- create memory with the handle name.
		- memory address is copied to the handle
		- loads the properties and initialize them with default values

**Polymorphism** - [[polymorphism|Polymorphism]] in SystemVerilog is when a virtual method call is resolved at run time based on the actual object type, not the handle type.

**overriding Constructor** - Override the default constructor
```systemverilog
function new(input string a = "default_string");
	$display("This is a string passed= %s", a);
endfunction
```

