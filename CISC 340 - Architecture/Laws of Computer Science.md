## Moore's Law
- "Prediction" made by Gordon Moore (co-founder of Intel) in 1965
- The number of transistors in a dense integrated circuit doubles about every two years
- Limits
	- Physical limits - have gotten as small as human hair -- any smaller and they will run into physics issues
	- Heat and power constraints - the denser transistors are, the harder they are to power/cool economically
- Potential advancements
	- Multiple cores
	- Specialized architectures
	- Quantum Computing
	- Sprintronics
	- Optical computing
## Amdahl's Law
- Formula to assess the potential speed up of a program via parallelization
![[Pasted image 20230912175727.png | 400]]
	- Speed up - improvement in execution time from parallelization
		- Note: denominator is the number of seconds divided by 100 (get seconds by multiplying by 100)
	- P - fraction/percent of program that can be parallelized
	- N - number of processors or core used for parallel execution
		- eventual limits of number of cores
- Speed up will always be limited
	- Limited by fraction of program being parallelized
	- Diminishing returns on cores
		- The more cores added, the potential for speed up lessens
		- Eventually it probably takes more time to distribute the program over the large number of cores