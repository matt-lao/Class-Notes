The questions below refer to this MIPS procedure that sums the values in an array of integers. It expects the array's address in `$a0` and the number of items to average in `$a1`.

```mips
1 sum: addi $sp, $sp, -8 # create room on the stack   
2 sw $s0, 0($sp) # save $s registers   
3 sw $s1, 4($sp)   
4 li $s0, 0 # Initialize loop counter   
5 li $s1, 0 # Initialize the sum   
6 loop: beq $s0, $a1, end # Leave if counter hits length   
7 sll $t0, $s0, 2 # $t0 = counter * 4   
8 add $t1, $t0, $a0 # $t1 = ($s0 * 4) + base address   
9 lw $t2, 0($t1) # $t2 = a[$s0]   
10 add $s1, $s1, $t2 # sum += a[$s0]   
11 addi $s0, $s0, 1 # counter++   
12 j loop   
13 end: move $v0, $s1 # put the result in $v0   
14 lw $s0, 0($sp) # restore $s registers   
15 lw $s1, 4($sp)   
16 addi $sp, $sp, 8 # pop the stack   
17 jr $ra
```

# Question 1

How many _instructions_ would be executed if the procedure were called to sum the items in an array of length 100?

**Answer:**
- Instructions 1-5 & 13-17 will only execute once, for a total of 10 non-loop instructions.
- Instructions 6-12 will execute 100 times, with the 6th instruction (`beq`) executing an extra time to exit the loop, for a total of 701 looped instructions.

Thus, a total of **711 instructions** will be executed in this procedure.

# Question 2

Assuming we don't pipeline and therefore have a clock period of 800 picoseconds (as shown in the following figure), how long would it take to run the procedure on the array of length 100 (hint: pay attention to the loop)?
![[Pasted image 20231205145520.png | 600]]

Answer:
	Since we have 711 instructions and each instruction takes a clock period of 800 picoseconds, we can do the following calculation.
$$ 711 \text{ Instructions} \times 8 \cdot 10^{-10} \text{ seconds} = 5.688 \cdot 10^{-7} \text { seconds}$$
	So the procedure would take $5.688 \cdot 10^{-7} \text{ seconds}$ or $568,800 \text{ picoseconds}$ to run.

# Question 3

Assume we execute the same call to `sum` on a processor that implements pipelining and has the pipeline stages and 200 picosecond clock period, as shown below. How long would it take to sum the array if there were no stalls (`nop` instructions) needed to be inserted (-- this isn't possible, but you should assume it is)?

![[Pasted image 20231205150733.png | 600]]

Answer:
	Since every clock period corresponds to a pipeline stage, at the end of each clock period a new instruction is issued (assuming no stalls). This continues until we reach the final instruction, where four more clock periods are needed to finish it. We can model this using the following calculation below,
$$ 711 \text{ instructions} \times 2 \cdot 10^{-10} \text{ seconds} + (4 \text{ pipeline stages} \times 2 \cdot 10^{-10} \text{ seconds}) = 1.43 \cdot 10^{-10} \text{ seconds} $$
	So this pipelined procedure would take $1.43 \cdot 10^{-10} \text{ seconds}$ or $143,000 \text{ picoseconds}$ to run.

# Question 4

Show where `nop` instructions would have to be inserted in the code above if it were to be successfully pipelined on a processor that did _not_ implement forwarding or branch prediction (assume all control hazards take 3 `nop`s to resolve). You should copy the code and insert the `nop` instructions. Do not reorder any of the instructions for this problem.

```mips
1 sum: addi $sp, $sp, -8 # create room on the stack   
2 nop
3 nop
4 sw $s0, 0($sp) # save $s registers   
5 sw $s1, 4($sp)   
6 li $s0, 0 # Initialize loop counter   
7 li $s1, 0 # Initialize the sum   
8 nop
9 loop: beq $s0, $a1, end # Leave if counter hits length   
10 nop
11 nop
12 nop
13 sll $t0, $s0, 2 # $t0 = counter * 4   
14 nop
15 nop
16 add $t1, $t0, $a0 # $t1 = ($s0 * 4) + base address   
17 nop
18 nop
19 lw $t2, 0($t1) # $t2 = a[$s0]   
20 nop
21 nop
22 add $s1, $s1, $t2 # sum += a[$s0]   
23 addi $s0, $s0, 1 # counter++   
24 nop
25 j loop   
26 end: move $v0, $s1 # put the result in $v0   
27 lw $s0, 0($sp) # restore $s registers   
28 lw $s1, 4($sp)   
29 addi $sp, $sp, 8 # pop the stack   
30 jr $ra
```

# Question 5

Show where `nop` instructions would have to be inserted in the original code if it were to be successfully pipelined on a processor that implements both flavors of forwarding (ALU to ALU, and MEM to ALU) but not branch prediction.  This should be yet another copy of the code (Again, don't get fancy, and DON'T try to hoist any instructions.)

```mips
1 sum: addi $sp, $sp, -8 # create room on the stack   
2 sw $s0, 0($sp) # save $s registers   
3 sw $s1, 4($sp)   
4 li $s0, 0 # Initialize loop counter   
5 li $s1, 0 # Initialize the sum   
6 loop: beq $s0, $a1, end # Leave if counter hits length   
7 nop
8 nop
9 nop
10 sll $t0, $s0, 2 # $t0 = counter * 4   
11 add $t1, $t0, $a0 # $t1 = ($s0 * 4) + base address   
12 lw $t2, 0($t1) # $t2 = a[$s0]   
13 nop
14 add $s1, $s1, $t2 # sum += a[$s0]   
15 addi $s0, $s0, 1 # counter++  
16 j loop   
17 end: move $v0, $s1 # put the result in $v0   
18 lw $s0, 0($sp) # restore $s registers   
19 lw $s1, 4($sp)   
20 addi $sp, $sp, 8 # pop the stack   
21 jr $ra
```
# Question 6

Ok, _now_ you can get fancy: Identify which `nop`s (by line number) from your answer to the previous problem (if any) could be filled by hoisting instructions.  Show the resulting procedure with the hoisted instructions.

Answer:
	The `nop` on line 13 can be filled by hoisting the instruction on line 15.

```mips
1 sum: addi $sp, $sp, -8 # create room on the stack   
2 sw $s0, 0($sp) # save $s registers   
3 sw $s1, 4($sp)   
4 li $s0, 0 # Initialize loop counter   
5 li $s1, 0 # Initialize the sum   
6 loop: beq $s0, $a1, end # Leave if counter hits length   
7 nop
8 nop
9 nop
10 sll $t0, $s0, 2 # $t0 = counter * 4   
11 add $t1, $t0, $a0 # $t1 = ($s0 * 4) + base address   
12 lw $t2, 0($t1) # $t2 = a[$s0]   
13 addi $s0, $s0, 1 # counter++ 
14 add $s1, $s1, $t2 # sum += a[$s0]   
15 j loop   
16 end: move $v0, $s1 # put the result in $v0   
17 lw $s0, 0($sp) # restore $s registers   
18 lw $s1, 4($sp)   
19 addi $sp, $sp, 8 # pop the stack   
20 jr $ra
```
