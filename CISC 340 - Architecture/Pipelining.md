![[Pasted image 20231120205045.png | 600]]
*Single Cycle Data Path*

These instructions all take one cycle.

It turns out the *Load Word* is our most expensive instruction.

# Fragmenting The Data Path

We can breakup the data path into five basic pieces:

**Fetch** (IF)
- Supply address to instruction memory
- Allow time for memory to supply the value

**Decode** (ID)
- Give the control blob time to determine settings
- Allow time for the register file to supply values

**Execute** (EX)
- ALU does its specified calculation

**Memory Access** (MEM)
- Time is needed to access main memory

**Write Back** (WB)
- Store results in memory or register

![[Pasted image 20231120205711.png]]

# Instructions & Parts

Not all instructions use all stages

**R-Type**: IF/ID/EX/WB (No MEM)
**LW**: IF/ID/EX/MEM/WB
**SW**: IF/ID/EX/MEM (No WB)
**BEQ**: IF/ID/EX (No MEM, WB)

All instructions have PC+4 does in the first stage (IF).

# Pipelining

Goal is to maximize the utilization of each stage in the process -- always be using the hardware.

Laundry analogy: Similar to 4 stages of "doing laundry", when one stage is done, you can start the one previous to it.

![[Pasted image 20231120210634.png]]

# MIPS & Pipelining

Fixed length instructions are used in MIPS, which:
- Makes fetching & decoding simple
- Makes the process the exact same for any instruction

Simple formats so many parts of an instruction can be done back to back.
