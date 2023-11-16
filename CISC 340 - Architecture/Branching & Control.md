The following data path can only execute instructions sequentially.

![[Pasted image 20231115231012.png]]

# Branching

`beq` is an i-type instruction, where the label is a signed offset.

The offset is calculated in reference from the instruction immediately following the `beq` instruction, and is the number of instructions (not bytes).
- A jump to previous instruction would be encoded as a negative number of instructions.
- A jump to a future instruction would be encoded as a positive number of instructions
# Calculating the Address

`Offset` will need to be sign extended to 32-bits, and multiplied by 4 to be converted from word to bytes.

The address of the instruction following `beq` can be extracted from PC's adder.

# Branching Address Calculation Data Path

`Offset` goes to a shifter to be multiplied by 4, then sent to a separate adder to be added to the result of `PC + 4`.

![[Pasted image 20231115232029.png | 600]]

# Controlling the Branch

Mux is used to control whether the `branch target` or `PC + 4` is piped into PC.

![[Pasted image 20231115232315.png]]

`PCSrc` is the control line that selects whether we branch or not.

# Control Blob

The control blob regulates the control lines for all our hardware. This blob gets the data on what the type of instruction is being used (opcode) and sets up our mux accordingly.

For branch control, an `AND` is performed between the `branch` line and the `zero` line. `Zero` will be an indicator if the values were equal, and the `branch` line will be active if the instruction is a branch type.

There are 9 lines coming from the control blob.

![[Pasted image 20231115232445.png]]

# ALU Control

`ALU Control` is a secondary control that gets data from the control blob and the `funct` bits (0-5).

There are 4 output lines from the `ALU Control`.

# ALU Op

`ALUOp` is set to: 
- 10 (2 in binary) by control blob if instruction is an R-type. The `Funct` bits determine the specific ALU operation.
- 00 (0 in binary) by control blob if instruction is `lw` or `sw`, since those bits make up the offset.
- 01 (1 in binary) by control blob if instruction is `beq`, since branching needs the `zero` output from the ALU, or in other words, the result of subtracting/checking equal.

# Instruction Types

For an R-type instruction, all operands are Registers