## CPU Time
- Wall time is not always a fair measure of how well a computer executes a task
- CPU Time measures exactly the time a process was "on the CPU"

#### Example
Assume a program executes 1 million instructions and that each instruction takes 1 clock cycle to execute.  How long would it take for the program to finish on a 2.1 GHz machine?  How about a 5.1 GHz machine?
##### Solution
- Clock rate is $2.1$ GHz $= 2.1 \cdot 10^9$ or $2.1 \cdot 10^9$ cycles per second
- Convert to seconds per cycle (Clock period = $1/$Hz)
	$\frac {1}{2.1\cdot10^9}$ Hz = $4.76 \cdot 10^{-10}$ seconds = $476$ picoseconds
-  Multiply by # of cycles
	CPU Time = $1,000,000$ cycles (instructions) $\cdot 4.76 \cdot 10^{-10}$ seconds


## Performances
- We compare computers using CPU time
- Smaller CPU time is better than larger one
	-> Performance = 1/CPU Time (to make it easier)

## Formulas
- Clock Rate (or Frequency) = GHz = $10^9$Hz
- Clock Period = 1/Clock Rate
- CPU Time = numCycles * Clock Period
	- = numCycles/Clock Rate (substitute for clock period)
- Performance = 1/CPU time
	- 1/(numCycles/Clock Rate)
	- Clock Rate/ numCycles

So, Performance is: Clock Rate/numCycles

## Calculating Cycles
- Unfortunately not all instructions take one cycle
- We need to take CPI into account (Cycles Per Instruction)
	- Hard to do for large programs -> Use Average CPI
- Updated formula
	- CPU Time = numCycles/Clock Rate
	- = numInstructions * CPI / clock rate

#### Example 
![[Pasted image 20230912174330.png]]
##### Solution
- Machine B
- 4.54 GHz