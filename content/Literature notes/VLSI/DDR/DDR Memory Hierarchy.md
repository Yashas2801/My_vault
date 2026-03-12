2026-03-10 16:00
Status: #done
Tags: #ddr #vlsi #memory #hierarchy

The DDR memory hierarchy defines the structural organization of memory from the outer system view down to the individual physical storage cells. Understanding this map is essential because it dictates how logical system addresses are translated into physical commands, directly determining bandwidth, parallelism, and latency.

- *See also:* [[DDR memory hierarchy]]

## 1. The Big Picture

When a memory address is issued, it traverses this exact path:

```text
CPU / SoC
   |
   v
DDR Controller
   |
   v
Channel
   |
   v
DIMM / SoDIMM
   |
   v
Rank
   |
   v
Chip 0   Chip 1   Chip 2  ... Chip N
   |        |        |
   +--------+--------+----> together form wide data bus
               |
               v
         inside each chip:
         Bank Group
             |
             v
            Bank
             |
             v
            Row   <-- ACT opens this whole row
             |
             v
          Column  <-- RD/WR selects starting column
             |
             v
         Burst on DQ bus
```

---

## 2. Channel

### Definition
A single, independent physical data and command path between the memory controller and the memory modules.
### What question it answers
How many independent memory traffic roads exist between the CPU and the RAM?
### Why it exists
To increase total system bandwidth by allowing parallel, concurrent memory requests across multiple distinct paths.
### Why it matters
More channels = more parallelism. A dual-channel system is like having two separate highways, doubling theoretical traffic capacity.

---

## 3. DIMM / SoDIMM

### Definition
Dual In-line Memory Module. The physical printed circuit board that you plug into the motherboard.
### What question it answers
What is the physical "stick of RAM" made of?
### Why it exists
To group multiple small DRAM chips together into a standardized, easy-to-install physical form factor.
### Why it matters
It is the delivery vehicle for Ranks. A DIMM is not one giant memory chip; it is a board carrying multiple DRAM devices working together.

---

## 4. Rank

### Definition
A group of multiple DRAM chips on a DIMM that are selected together and behave like one single, wider memory unit.
### What question it answers
How do we get a 64-bit wide data bus when individual chips are only 8 bits wide?
### Why it exists
Individual memory chips are narrow. By grouping 8 chips of x8 width together and accessing them simultaneously, the system gets a full 64-bit word in one go.
### Why it matters
A rank is the foundational unit of data width. Accessing a rank means accessing multiple chips at the exact same time.

- *See also:* [[Rank]]

---

## 5. Chip width (x4 / x8 / x16)

### Definition
The classification of a single DRAM device based on its internal Data (DQ) bus width.
### What question it answers
How many bits of data does one individual chip output per transfer?
### Why it exists
To allow flexibility in building modules. A 64-bit rank can be built using sixteen x4 chips, eight x8 chips, or four x16 chips.
### Why it matters
Chip width dictates how many physical chips are required to saturate the channel's data bus. 

---

## 6. Bank Group

### Definition
A cluster of Banks inside a single DRAM chip that share certain internal routing logic.
### What question it answers
How is the chip organized internally to allow faster back-to-back accesses?
### Why it exists
To support more concurrency. Accessing different bank groups faces fewer timing restrictions than repeatedly accessing the same bank group.
### Why it matters
Bank groups are a key architectural feature (introduced heavily in DDR4) to improve memory bandwidth and parallelism.

---

## 7. Bank

### Definition
The core working unit for commands inside the chip, containing its own memory array and its own Sense Amplifiers (Row Buffer).
### What question it answers
Where does the actual activation of a row happen?
### Why it exists
To allow multiple different rows to be open simultaneously across the chip (one open row per bank). 
### Why it matters
**One bank can only have one active row at a time.** If you need a new row in the same bank, you must close the old one first. A bank is like a file drawer where only one folder can be pulled out at a time.

- *See also:* [[Bank]]

---

## 8. Row

### Definition
A full horizontal slice of memory cells within a bank.
### What question it answers
What chunk of data is loaded into the Sense Amplifiers when an `ACT` command is sent?
### Why it exists
DRAM cannot read individual bits directly from the array. It must activate a whole row of cells, dumping their charge into the sense amplifiers.
### Why it matters
Opening a row takes time (`tRCD`). Once open, it serves as a temporary cache (Row Buffer) for fast column accesses.

- *See also:* [[Row buffer]]

---

## 9. Column

### Definition
A vertical slice that selects a specific piece of data from the currently open row.
### What question it answers
Which exact bytes within the massive open row do I actually want to read or write?
### Why it exists
An open row is massive (e.g., thousands of bits). The CPU only needs a small chunk (e.g., 64 bytes) at a time.
### Why it matters
The `RD` or `WR` command targets a column. It is the final coordinate in the memory map.

- *See also:* [[Column access]]

---

## 10. Burst Length

### Definition
The number of consecutive data beats transmitted back-to-back on the data bus from a single `RD` or `WR` command.
### What question it answers
Does DDR send just one bit and stop?
### Why it exists
To maximize bus efficiency. Sending an address takes time; once the location is found, it is faster to burst out a continuous chunk of data.
### Why it matters
In DDR4 (BL8), one read command bursts 8 beats of data. For a 64-bit rank, this results in a single transfer of 64 bytes (8 beats × 8 bytes).

- *See also:* [[Burst length]]

---

## 11. Full Hierarchy Example

If the controller receives a memory address, it decodes it down the hierarchy:

```text
System Address
   -> Channel 0
       -> Rank 0
           -> Bank Group 2
               -> Bank 1
                   -> Row 120
                       -> Column 40
```

---

## 12. Command Connection

The physical hierarchy maps perfectly to the DDR command sequence:

1. **ACT (Activate):** Targets the **Bank** and opens the **Row** into the row buffer.
2. *(Wait `tRCD`)*
3. **RD / WR (Read/Write):** Targets the starting **Column** within that already-open row. Data bursts out.
4. **PRE (Precharge):** Closes the active row inside that specific **Bank** to prepare it for a future ACT.

---

## 13. Performance Intuition

Memory latency heavily depends on what is currently open in the **Bank**:

### 1. Same Bank, Same Open Row (Fastest)
* **State:** Bank 1 has Row 120 open. Request needs Row 120, Col 40.
* **Action:** Issue `RD/WR` immediately. (Row Hit)

### 2. Same Bank, Different Row (Slowest)
* **State:** Bank 1 has Row 120 open. Request needs Row 300, Col 12.
* **Action:** Must issue `PRE` (close Row 120) -> `ACT` (open Row 300) -> `RD/WR` (Col 12). (Row Miss)

### 3. Different Bank (Parallel)
* **State:** Bank 1 is busy. Request needs data from Bank 3.
* **Action:** Controller works on Bank 3 concurrently while Bank 1 finishes. (Bank-Level Parallelism)

---

## Key Takeaways
* Address decoding flows from Channel → Rank → Bank Group → Bank → Row → Column.
* A Rank is a team of chips acting as one wide memory unit; it is not a single chip.
* An `ACT` command opens an entire Row.
* A `RD` or `WR` command targets a Column within an already open Row.
* A Bank can only hold one Row open at a time.
* Data is returned in Bursts (e.g., 8 beats), not single bits.

## Common Confusions
* **Rank vs. Chip:** A rank is *not* one chip. It is a collection of chips (e.g., eight x8 chips) working in parallel to form a 64-bit bus.
* **ACT opens a column:** False. `ACT` opens a massive *Row*. `RD/WR` selects the *Column*.
* **Multiple open rows:** One Bank *cannot* keep multiple rows open at once. It has only one Row Buffer.
* **Single bit transfers:** Burst length means a single `RD` command results in multiple consecutive beats of data across the bus.

---

## Quick Self-Test
1. Is a rank one chip or many chips working together?
2. When `ACT` is issued, does it open a column or a row?
3. Can one bank have two rows open at once?
4. What does `RD/WR` choose after a row is open?
5. Why do more banks and bank groups help performance?

*(Answers: 1. Many chips; 2. A row; 3. No; 4. A specific column; 5. They allow bank-level parallelism/concurrency)*

---

## 30-Second Revision
Memory requests travel: **Channel** (the road) -> **Rank** (team of chips) -> **Bank Group/Bank** (the file drawer) -> **Row** (the opened file) -> **Column** (the specific word). `ACT` opens the row, `RD/WR` reads columns in bursts, and `PRE` closes the row. You can only have one row open per bank at a time.