2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

# Row buffer

### Definition
The array of Sense Amplifiers inside a Bank that detects, amplifies, and temporarily holds the entire contents of an activated memory Row.

### Question it answers
Where does the data sit between being pulled from the raw analog cells and being sent over the digital data bus?

### Why it exists
DRAM cells have tiny, fragile charges. They cannot be read directly bit-by-bit. An entire row must be dumped into the robust Sense Amplifiers (the Row Buffer) to stabilize the data so it can be safely read or written.

### Importance
The Row Buffer acts like a tiny, extremely fast cache for the Bank. 
If subsequent memory requests target the same row currently held in the Row Buffer ("Row Hit"), data is returned extremely quickly.

### Related Notes
* [[ACT opens a row into the row buffer|ACT]]
* [[Bank]]
* [[DDR - Row buffer and sense amplifiers]]
