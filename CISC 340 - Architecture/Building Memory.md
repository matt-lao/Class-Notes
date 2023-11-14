- Registers are 32 memory units (where one unit holds a bit of information).
- The issue we have to overcome is that circuits will **forget**.
---
# Circuit That Remembers

![[Pasted image 20231113160041.png | 500]]

The output of an OR gate can be routed back to itself, however this keeps the circuit on indefinitely.

---
# Memory That Can Be Reset

![[Pasted image 20231113160617.png]]
*This circuit is Set-Reset Latch or SR Latch.*

An second input to reset the input can fix the circuit staying on indefinitely. However, there is an invalid case where both *set* and *reset* are on.

The issue here lies in conceptualizing our inputs as switches. Inputs to a circuit are more like button presses, that do not sustain long after they have been triggered.

In an SR Latch, the reset switch is actually a *clock*.

---
# Clock

![[Pasted image 20231113161440.png]]

The clock is used to synchronize the processor. It is an oscillator that send alternating high and low voltage signals.

The wave form above is a "square" waveform.
- High Signal - 1
- Low Signal - 0 
---
# Data Latch (D-Latch)

![[Pasted image 20231113162155.png]]

Data is sampled only when the clock is in the high position (1).

Two problems:
1. Clock high value is a long time, which means the data has to remain constant.
2. Result could change every clock cycle.
---
# Edge Trigger

![[Pasted image 20231113162605.png]]

Sample only on the rising edge of the clock. There is physical delay in the gates which can be used to create a rising edge detector.

![[Pasted image 20231113162416.png | 600]]
*Logically, the output will always be 0.*

The physical delay in the NOT gate will allow for the output data line to be 1 for a brief moment.

--- 
# D Flip-Flop

![[Pasted image 20231113163107.png]]
*D-Latch with a rising edge detector.*

We want all values to be set/sampled at the same time. Subsequently, calculations and background processes will happen during the following clock period (rising edge to next rising edge). 

---
# Controlling The Sampling

`Write` controls whether the register is written to or not.

![[Pasted image 20231113163921.png]]

Each register is just 32 D Flip-Flops

![[Pasted image 20231113164029.png | 500]]