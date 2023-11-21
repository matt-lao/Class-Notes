
# Challenges To Pipelining

- Branching makes next instruction obscure
- Interdependent instructions
- Needing to use same hardware at same time

The issues lead to *hazards*.

Hazard implies that the next instruction needs to be delayed before it starts.

# Structural Hazards

Two instructions require the same functional unit on the CPU.

Can avoid by delaying the second instruction.

![[Pasted image 20231120230049.png | 500]]

In this example, the hazard is that both I1 and I4 (WB and ID) are accessing the register file at the same time.

Luckily neither require a full cycle to complete, so we can write to a register in the first half of the cycle and read in the second half (save from using a NOP). 

# Memory Structural Hazard

Another structural hazard is accessing IF and MEM at the same time since technically instruction memory and main memory are the same.

The fix for this is using **Dual-Port RAM**, which allows for multiple reads and writes at the same time.

![[Pasted image 20231120230531.png | 400]]

# Data Hazard

Results from dependencies between instructions.

```mips
add $s0, $t0, $t1
addi $s0, $s0, 5
```

The use of a destination register in the next consecutive call is a dependency that needs a delay so `$s0` can be written back to.

The stalling of instructions is represented with NOPs. For data hazards we only need to stall until the WB stage, since we can write in the first half of the period and read in the second half.

# Control Hazard

Occur when it is not possible to know what the next instruction should be.

```mips
	beq $s0, $s1, dest
	add $s0, $s0, $s1
dest:
	move $v0, $s0
```

`beq` requires a delay until we know weather `$s0` is equal to `$s1`, which happens in the MEM phase.

We again need to stall until the MEM stage is fully completed.

