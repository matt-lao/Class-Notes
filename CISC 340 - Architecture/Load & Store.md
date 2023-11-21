# Main Memory

Load & Store commands interact with main memory, which is built out of Dynamic RAM (DRAM).

DRAM is not made out of D Flip-Flops like registers are. They are built with transistors and capacitors.

The capacitors are able to be charged and discharged (1 or 0), however they gradually leak their charge creating the need to be periodically refreshed. 

The transistor is used to regulate currents during writes and reads.

![[Pasted image 20231115223645.png | 400]]

Takes two inputs
- Memory address
- Data to be written (store word only)

Returns the data when loading a word.

# Generating The Address

![[Pasted image 20231115223907.png]]

- `rt` is the register containing the value to be stored in memory
- `rs` + `offset` makes up the memory address to write/load from

The 16 bit `offset` goes through a sign extension to 32 bits before being added to the `rs`

![[Pasted image 20231115224317.png | 400]]

Remember, sign extension takes the MSB and extends it (repeats it) all the way to the 32nd bit.

# Address Calculation Path

The `offset` and `rs` are added using the ALU.

![[Pasted image 20231115225036.png | 500]]

`Offset` is extracted from the instruction before entering the register file. It is then subsequently sign extended and sent to the ALU

`rs` flows to the the ALU as the first operand. 

A mux is added for the second operand to selected between the operand coming from the register file and the `offset`.

# Connect to Main Memory

The ALU result will have a line split to be piped into `address` input for main memory.

The data read from `rt` (register 2) will have a line split before the `ALUSrc` mux to pipe it into the `data` input for main memory

![[Pasted image 20231115225540.png | 600]]

`Read data 2` will also be sent to `write data` but will be blocked by the `RegWrite` which will have 
a value of 0.

# Load Word

![[Pasted image 20231115225956.png]]

The difference with load word is that `rt` is a destination register, so data will written to it instead of read from it.

Value from main memory will now be written to a register.

# Load Word Path

The `rd` register has a mux in front of it to either be the true `rd` register for an r-type instruction, or take the value of the `rt` register to be the destination register for an i-type instruction.

ALU result line has a mux with the data read from main memory. 

Control lines for `MemWrite` & `MemRead`.

# Complete Load/Store Data Path

![[Pasted image 20231115230808.png]]

# Read v. Write Control Lines

Write control lines always matter when executing instructions that are unrelated to actual write operations.

Read control lines are trivial when executing instructions that are unrelated to actual read operations.

