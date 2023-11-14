## Game Theory 
- Axes
	- Deterministic or stochastic? 
	- One, two, or more players? 
	- Zero sum?
	- Perfect information (can you see the state)?
- Deterministic Games
	- Formalization
		- States: S (start at $s_0$ ) 
		- Players: P={1...N} (usually take turns) 
		- Actions: A (may depend on player / state) 
		- Transition Function: S x A → S 
		- Terminal Test: S → {t,f} 
		- Terminal Utilities: S x P → R
	- Solution for a player is a **policy**: S → A
- Zero Sum
	- Opposing utilities between each player



## Adversarial Search
- Single-Agent Trees
	![[Pasted image 20230310141851.png]]
- Value of a state
	- Best possible utility that can be achieve from the current state
	- Tree is navigated by finding the maximum utility from the successor states


## Minmax Algorithm 
- Tree with an adversary
	![[Pasted image 20230310142742.png]]
	- Minimax Values
		- States under adversary's control -> will pick minimum values from the sucessors
		- States under agent's control -> will pick maximum values from the sucessors
- Minimax Search
	![[Pasted image 20230313135106.png]]
	- A state-space search tree
	- Players alternate turns
	- At each level of the tree each the min or max values are selected from the sucessors states
		- This represents choosing an optimal move
- Efficiency
	- Exhaustive (like DFS)
	- Time: $O(b^{n})$
	- Space: $O(bm)$
- Implementation
	![[Pasted image 20230315135505.png]]


## Alpha-Beta Tree Search 
- Avoiding branches that we know will be unsucessful
![[Pasted image 20230313141250.png]]
- The above graph does not explore some of the nodes that will not affect the minmax comparisons
- For min selection
	- Selects the first value that is less than smallest value selected prior
	- This is because the next level selects the largest value
- For max selection
	- Selects the first value that is greater than the largest value selected prior
	- This is because the the next level is selects the smallest value

## Expectimax Tress Search