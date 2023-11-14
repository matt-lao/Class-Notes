
![[Pasted image 20231113170806.png | 600]]

Register file takes three inputs for a number a register:
- Read register 1 (five bits)
- Read register 2 (five bits)
- Write register (five bits)

The register numbers come from the instructions.

Registers and their encoded values are in the register file.

![](Images/Pasted%20image%2020231113171025.png?raw=true)
![[Pasted image 20231113171207.png]]

The instructions live in memory. A PC register keeps tack of the address of the current instruction.

![[Pasted image 20231113171342.png]]
- Op1 = bits 25-21
- Op2 = bits 20-16
- Data # = bits 15-11

To get the next instruction, a line from the PC register is diverted to an adder that adds 4.

![[Pasted image 20231113171837.png | 600]]

The clock needs to orchestrates many tasks in this process
- Continuously updates register in PC
- Stores the newly computed value by asserting `RegWrite`

The following should all be able happen within a clock period:
- Instruction to be parsed into a register file
- Output values obtained from registers passed in
- ALU calculation
- Return result to register file
