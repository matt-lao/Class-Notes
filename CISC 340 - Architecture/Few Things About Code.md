## Languages Overview
- Machine Code
	- Lowest level
	- Binary representation of computer instructions that the CPU can execute
	- Specific to a single CPU architecture
- Assembly Language
	- One step above machine code
	- Uses symbolic names to represent the machine instructions
	- Still architecture specific
	- Uses **assembler** to translate assembly code to machine code
- High Level Languages
	- Java, C, C++, LISP, Python
		- Designed to be human readable
		- Portable across various architectures
		- Provide high productivity but lower efficiency -- translation
	- Running high level languages 
		- Computers can only execute machine code, so all programs must ultimately be translated to the appropriate binary
		- Complied or Interpreted

## Compilers
- Compiler - software tool that translates high-level source code to machine code
	- Generates object files which can be executables
- Compilers are custom built for each architecture
- Consists of multiple stages
	 ![[Pasted image 20230911171713.png | 300]]

## Interpreters
- Some languages are not compiled -> interpreted
- Interpreter: Software tool that directly executes high-level source code line by line
- No intermediate representation
- Very mobile but slower generally
![[Pasted image 20230911172046.png | 400]]

## Instruction Set Architecture (ISA)
- Compiled or Interpreted all the source code needs to be translated to machine code
- Machine code varies based on the CPU architecture
	- The set of instructions available to a computer is specified by the ISA
	- ISA can change between generations of processors
- Two main ISA types -- RISC and CISC
- 
- MIPS
	- Microprocessor without Interlocked Pipeline Stages
	- RISC architecture that uses three different instruction categories
		- I-Type, J-Type, R-Type
	- All instructions are the same number of bits, and they all take the same time to execute
	- Used for education in embedded systems
	- Example
		- Let's translate the following Java code to MIPS
			- x = 2 + 10 * y – z;
				```
```
				//Assume that that registers $a2 = x, $a3 = y, $a4 = z
				addi $t0, $zero, 10  //temp = 0 + 10
				mult $a2, $a3, $t0   //x = temp*y
				addi $a2, $a2, 2      //x = x + 2
				sub  $a2, $a2, $a4  //x = x - z
