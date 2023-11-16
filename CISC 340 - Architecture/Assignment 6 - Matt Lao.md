
# Question 1

The goal for this problem is to design and implement a circuit that's similar to a multiplexer, but has two outputs instead of one. (See diagram below.) If the `select` input is a 0, the circuit is in "pass-through" mode (dotted lines), so `out1 = a` and `out2 = b`. If `select` is a 1, the circuit is in "cross-over" mode (dashed lines), so `out1 = b` and `out2 = a`.

![[Pasted image 20231114072407.png | 300]]

The truth table for this circuit is as follows:

| a | b | Select | out1 | out2 |
|---|---|--------|-------|-------|
| 0 | 0 |   0    |   0   |   0   |
| 0 | 0 |   1    |   0   |   0   |
| 0 | 1 | 0 | 0 | 1 |
| 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 |

The following is the simplification for `out1`:
$$ \text{out1} = \bar{a} \cdot b \cdot \text{Select} + a \cdot \bar{b} \cdot \bar{\text{Select}} + a \cdot b \cdot \bar{\text{Select}} + a \cdot b \cdot \text{Select} $$
$$ \text{out1} = a \cdot \bar{\text{Select}} \cdot (\bar{b} + b) + b \cdot \text{Select}\cdot(\bar{a}+a) $$
$$ \underline{\text{out1} = a \cdot \bar{\text{Select}} + b \cdot \text{Select}}$$
The following is the simplification for `out2`:
$$\text{out2} = \bar{a} \cdot b \cdot \bar{\text{Select}} + a \cdot \bar{b} \cdot \text{Select} + a \cdot b \cdot \bar{\text{Select}} + a \cdot b \cdot \text{Select}$$
$$ \text{out2} = b \cdot \bar{\text{Select}} \cdot (\bar{a} + a) + a \cdot \text{Select} \cdot (\bar{b} + b)$$
$$ \underline{\text{out2} = a \cdot \text{Select} + b \cdot \bar{\text{Select}}}$$
Here is the the circuit diagram for the for the Boolean Formula's:

![[Circuit Diagram Assignment 6 Annotated.jpg]]


# Question 2

### Set Less Than:

- $\text{A}_{\text{invert}}$ = 0
- $\text{B}_{\text{invert}}$ =1
	- We want to subtract $\text{B}$ from $\text{A}$, so we do this by inverting the bits of $\text{B}$.
- $\text{Operation}$ = 3
	- 3 is the `Operation` input that selects the `Less` input from the mux. The `Less` input for the ALU for the LSB gets the MSB from the subtraction $\text{A} - \text{B}$. The `Less` inputs for the other 31 ALUs are 0. These `Less` inputs are directly outputted as the `Result`.

### NAND:

- $\text{A}_{\text{invert}}$ = 1
- $\text{B}_{\text{invert}}$ =1
- $\text{Operation}$ = 1

1 is the `Operation` input that selects the result of `OR` from the mux. We invert both operand inputs, and by De Morgan's Law, this is the same as performing a `NOT` on the result of $A \cdot B$ (in other words, $\bar{A} + \bar{B} = \bar{(A \cdot B)}$). 

### Equal:

- $\text{A}_{\text{invert}}$ = 0
- $\text{B}_{\text{invert}}$ =1
- $\text{Operation}$ = 2

2 is the `Operation` input that selects the result of adding the bits of $A$ and $B$ together. We invert the bits of $B$ because if $A+(-B)$ is 0, then $A = B$. Are ALU performs an `AND` operation on all the result bits, and then performs a `NOT` on the subsequent output. This output is our `Zero` output which is checked for equality. If the value of `Zero` is 1, they are equal, and if it is 0, they are not.

### Subtraction

- $\text{A}_{\text{invert}}$ = 0
- $\text{B}_{\text{invert}}$ =1
- $\text{Operation}$ = 2

2 is the `Operation` input that selects the result of adding the bits of $A$ and $B$ together. We invert the bits of $B$ because we want to perform the operation $A+(-B)$ on all the bits of $A$ and $B$. This is similar to equality, however, the result of subtraction is output to the result bits which is where the value of $A-B$ resides.