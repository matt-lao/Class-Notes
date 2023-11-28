One approach to a control hazard is issuing three NOPs so the address of the instruction to branch to has time to be recalled.

![[Pasted image 20231127172512.png]]

Equality hardware can be added to quickly if the two register values are equal in the ID phase. Target calculation can happen in the ID phase as well too.

Now only one NOP is needed.

![[Pasted image 20231127172758.png]]

However CPI is still affected by a NOP, (loops).

# Static Branch Prediction

Assume branch is always not taken based on context.  The compiler optimizes for this,  and rearranges code to maximize success.

# Dynamic Branch Prediction

Use the history of what was done at the branch instruction last time.

- One bit
	- Starts in the off position - 0
	- For a loop, will be wrong initially and then wrong again at the last iteration
	- Mispredicts a lot for nested structures
- Two bit
	- Have to be wrong twice before the state changes
	- Better captures the behavior of branches that often do the same thing

![[Pasted image 20231128074039.png]]

# Misprediction

If prediction is wrong, we flush the instruction (from the stage buffer) we fetched and start with the correct one.

This requires our hazard hardware to detect mispredictions.
