#### Depth-Limited Search
- DFS but stopping when getting to a certain depth level
- Context of the problem can suggest what maximum depth level we should use

#### Iterative Deepening
- Run a DFS with depth limit 1, then depth limit 2 and so on
- Has 11% more overhead when compared to DLS

#### Cost-Sensitive Search
- Similar to Djisktra's algorithm
- Searches by edge weight
- Uses cost-contours rather than levels

# Informed Search
#### Best First Search
- Uses tree/graph search algorithm
- Nodes selected for expansion beased on an **evalutation function**
	- Evaluation functions
		- f(n) - evaluation function
		- g(n) - cost function
		- h(n) - heuristic function
	- UCS
		- f(n) = g(n)
	- Greedy best first search
		- f(n) = h(n)
	- A* search
		- f(n) = g(n) + h(n)

#### Search Heuristics
- A function that *estimates* how close a state is to goal
- Designed for particular serach problem
- Example - manhattan/euclidean distance (distance regardless if a path exists)
- Pancake Problem
	- Can create a state space graph of different states of a pancake state
		- ![[Pasted image 20230222135107.png]]
		 - Heuristic Function?
			 - Heuristics
				 - The number of panckaes that are still out of place
				 - The number of the largest pancake that is still out of place

#### Greedy Search
- Expand node that you think is closest to a goal state
	- Heuristic - estimate of distance to nearest goal for each state
- Can lead to suboptimal solution
- "Focused depth first search"

#### A* Search
$$ f(n) = g(n) + h(n) $$
- Uses cost function and heuristic function to find optimal node to expand
	- Search is ordered by the sum of the cost according to uniform cost and greedy search
- Avoids expanding paths that are already expensive
- Teamwork approach
- Only end search when we actually expand goal node (not when it is in the fringe)
- Optimal?
	- Not optimal
		- When estimated costs are overestimating
	- Optimal
		- Estimated cost is lower than actual cost
- Admissible Heuristics
	- Heuristics that never overestimates cost to the goal state
	- A heuristic $h$ is admissible (optimistic) if:
$$ 0 \le h(n) \le h^{*}(n)$$
		where $h^{*}(n)$ is the true cost to a near goal
- **Optimality of A* tree search**
		![[Pasted image 20230224140751.png]]
	- Assume
		- A is an optimal goal node
		- B is a suboptimal goal node
		- h is admissible
	- Claim
		- A will exit the fringe before B
	- Proof
		- Imagine B is on the fringe
		- Some ancestor $n$ of A is on the fringe, too (maybe A itself)
		- Claim: $n$ will be expanded before B
			1. $f(n$) is less or equal to $f(A)$
			2. $f(A)$ is less than $f(B)$
			3. $n$ expands before B
		- All ancestors of A expand before B
		- A expands before B
		- A* search is optimal with admissible heuristic
- Properties of A* search
		![[Pasted image 20230224141808.png]]
	- A* more time and space efficient
	- Complete
	- Exponential time complexity
	- Keeps all nodes in memory
	- Optimal

#### Creating Heuristics (Admissible)
- When creating a heuristic solving the problem without constraints is helpful
	- Reveals new actions that are avialable
	- Ex: removing walls from the problem
	- This called a *relaxed problem*
	- This helps ensure that we are underestimating the actual cost with our heuristic
- 8 Puzzle Example
	![[Pasted image 20230227134238.png]]
	- Heurstic 1: Out of place tiles
		- Admissible
		- Not super efficient
	- Heurstic 2: Manhattan distance
		- Admissible
		- More efficient
	- Heurstic 3: Actual cost
		- Admissible (barely)
		- Do not save on nodes expanded
		- More work because we are comupting heurstic as well
- Trivial Heurstics??
	![[Pasted image 20230227134939.png]]
	- Any heurstic that is between exact cost and goal state is admissible
	- Note, max of two admissible heuristics is admissible


# Graph Search
- Tree search of different stat can lead to exponentially more work!
	- Cycles are harder to detect in trees
	- Solution for trees
		- Idea: Never expand a state (node) twice
		- Implementation
			- Tree Search + Set of expanded nodes
			- Before expanding next node, check to see if the node is already in the closed set
			- If it is in that set, skip it. If not, expand it.
		- Important to have **set** of expanded nodes rather than a list
#### Consistency of Heuristics
- Admissiblity: Heuristic cost is less than actual cost to goal state
- Consistency: Heurstic "node" cost is less than actual cost for each node relationship
- All consistent heurstics are admissible

# A* Summary
- Uses backward costs adn (estimates of) forward costs
- Optimal with admissible/consistent heuristics
- Heurstic desgin is key: use relaxed problems

