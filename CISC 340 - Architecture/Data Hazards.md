![[Pasted image 20231126181924.png]]
There are 19 cycles in this program, counted using the method above.

The number of instructions is the number of actual instructions.

Each stage of an instruction is a cycle (ex. IF = 1 cycle).

# Hoisting

One way to reduce the impact of data hazards is to rearrange independent instructions.

![[Pasted image 20231126182317.png | 300]]

# Forwarding

When a value is ready before being written to memory, it can be forwarded to the next set of instructions.

![[Pasted image 20231126182531.png]]

- **ALU to ALU forwarding** - the output from the ALU unit is piped into the ALU as an input
	- Used when the needed result is created by the ALU (add, sub, etc....)
	- EX to EX
- **MEM to ALU forwarding** - the output from memory unit is piped into the ALU as an input
	- Used when the needed result is being read from memory (lw)
	- Requires 1 NOP
	- Mem - NOP - EX

![[Pasted image 20231127170721.png]]

If we add hoisting to this we get an even better result.

![[Pasted image 20231127171006.png]]

$CPI = 11/7 = 1.57$
