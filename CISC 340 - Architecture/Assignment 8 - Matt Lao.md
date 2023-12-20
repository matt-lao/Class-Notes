## Question 1

For a direct-mapped cache design with a 32-bit address, the following bits of the address are used to access the cache.

|Tag|Index|block offset|byte offset|
|---|---|---|---|
|31-10|9-5|4-2|1-0|

What is the cache block size (in words)? How many entries does the cache have?

Answer:
	This direct-mapped cache has 32 entries and a block size of 8 words.

## Question 2

Consider these two lists of 32-bit memory address references, given as word addresses:

|Sequence|Addresses|
|---|---|
|a.|1, 134, 212, 1, 135, 213, 162, 161, 2, 44, 41, 221|
|b.|6, 214, 175, 214, 6, 84, 65, 174, 64, 105, 85, 215|

### Part A

For each of these references, identify the binary address, the tag, and the index given a direct-mapped cache with 16 one-word blocks.  

**Table A**

| Address | Tag | Index | Hit/Miss |
|---|---|---|---|
|1| 0000000000000000000000000000 | 0001 | Miss |
|134| 0000000000000000000000001000 | 0110 | Miss | 
|212| 0000000000000000000000001101| 0100 | Miss |
|1| 0000000000000000000000000000 | 0001 | Hit |
|135| 0000000000000000000000001000 | 0111 | Miss |
|213| 0000000000000000000000001101 | 0101 | Miss |
|162| 0000000000000000000000001010| 0010 | Miss | 
|161| 0000000000000000000000001010 | 0001 | Miss |  
|2| 0000000000000000000000000000 | 0010 | Miss | 
|44| 0000000000000000000000000010 | 1100 | Miss |
|41| 0000000000000000000000000010 | 1001 | Miss |
|221| 0000000000000000000000000010 | 1001 | Miss | 

**Table B**

| Address | Tag | Index | Hit/Miss |
|---|---|---|---|
|6| 0000000000000000000000000000 | 0110 | Miss |
|214| 0000000000000000000000001101 |0110 | Miss | 
|175| 0000000000000000000000001010 | 1111 | Miss |
|214| 0000000000000000000000001101 | 0110 | Hit |
|6| 0000000000000000000000000000 | 0110 | Miss |
|84| 0000000000000000000000000101| 0100 | Miss |
|64| 0000000000000000000000000100 | 0000 | Miss | 
|174| 0000000000000000000000001010 | 1110| Miss |  
|64| 0000000000000000000000000100 | 0000| Hit | 
|105|0000000000000000000000000110 | 1001 | Miss |
|85| 0000000000000000000000000101 | 0101 | Miss |
|215| 0000000000000000000000001101 | 0111| Miss | 

### Part B 

For each of these references, identify the binary address, the tag, and the index given a direct-mapped cache with two-word blocks and a total size of eight blocks.

**Table A**

| Address | Tag | Index | Block Offset | Hit/Miss |
|---|---|---|---| --- |
|1| 0000000000000000000000000000| 000 | 1 | Miss |
|134| 0000000000000000000000001000 | 011| 0 | Miss | 
|212| 0000000000000000000000001101| 010| 0 | Miss |
|1| 0000000000000000000000000000 | 000| 1 | Hit |
|135| 0000000000000000000000001000 | 011| 1 | Hit |
|213| 0000000000000000000000001101 | 010| 1 | Hit |
|162| 0000000000000000000000001010| 001| 0 | Miss | 
|161| 0000000000000000000000001010 | 000| 1 | Miss |  
|2| 0000000000000000000000000000 | 001| 0 | Hit | 
|44| 0000000000000000000000000010 | 110| 0 | Miss |
|41| 0000000000000000000000000010 | 100| 1 | Miss |
|221| 0000000000000000000000000010 | 100| 1 | Miss | 

**Table B**

| Address | Tag | Index | Block Offset | Hit/Miss |
|---|---|---|---|---| 
|6| 0000000000000000000000000000 | 011|0 | Miss |
|214| 0000000000000000000000001101 |011|0 | Miss | 
|175| 0000000000000000000000001010 | 111|1 | Miss |
|214| 0000000000000000000000001101 | 011|0 | Hit |
|6| 0000000000000000000000000000 | 011|0 | Miss |
|84| 0000000000000000000000000101| 010|0 | Miss |
|64| 0000000000000000000000000100 | 000|0 | Miss | 
|174| 0000000000000000000000001010 | 111|0| Hit |  
|64| 0000000000000000000000000100 | 000|0| Hit | 
|105|0000000000000000000000000110 | 100|1 | Miss |
|85| 0000000000000000000000000101 | 010|1 | Hit |
|215| 0000000000000000000000001101 | 011|1| Miss | 

## Question 3

|Base CPI (no memory stall)|Processor Speed|Main Memory Access time|L1 Cache Miss Rate Per  instruction|L2 Cache, Direct-Mapped Speed|Global Miss Rate with L2 Cache, Direct-mapped|L2 Cache, Eight-Way Set Associative Speed|Global Miss Rate with L2 Cache, Eight-Way Set Associative|
|---|---|---|---|---|---|---|---|
|1.5|2 GHz|100 ns|7%|12 cycles|3.5%|28 cycles|1.5%|

Calculate the CPI for the processor in the table using only a L1 cache. Note that you'll have to calculate how many cycles the main memory takes to access as its time is given in ns.

Answer: 
$$\text{CPI} = 1.5 + \frac{(0.07 \cdot 10^-7)}{2\cdot10^{-9}} $$
$$ CPI = 1.5 + 3.5 \cdot 10^{-18} $$

Calculate the CPI for the processor in the table using the L1 and L2 Direct Mapped caches.

Answer:
$$\text{CPI} = 1.5 + (0.07 * 12) + ((0.965 \cdot 12) + (0.035 \cdot 0.1 \cdot 2))$$
$$ \text{CPI} = 1.5 + 0.84 + 11.587 = 13.927 $$
Calculate the CPI for the processor in the table using the L1 and L2 Eight-Way Set Associative

Answer:
$$ \text{CPI} = 1.5 + (0.07\cdot28) + ((0.985\cdot28)+(0.035 \cdot 0.1 \cdot 2))  $$
$$ \text{CPI} = 1.5 + 1.96 + 0.07 = 27.5975 $$
