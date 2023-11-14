##### What is Search for?
- Assumptions
	- Single agent
	- Deterministic actions
	- Fully observed state
	- Discrete state space
- Planning - sequence of actions
	- The path to the goal is important
	- Paths have costs, depths
	- Heuristics give problem-specific guiance
- Identification - assignments to variables
	- Goal itself is important (not path)
		- Need a single goal state typically, not THE goal state (or all goal states)
	- All paths at same depth (for some formulations)
	- CSPs are specialized for identification problems

## <u>Defining constraints satisfaction problem</u> 
- Standard search problems
	- State is a "black box": arbitrary data structure
	-  Goal test can be any function over states
	- Successor function can also be anything
- Constraint satisfaction problems (CSPs)
	- Special subset of search problems
	- State defined by *variables* with values from a *domain*
		- Example: Scheduling meeting
			- Friends are variables (availability)
			- Domain are the times to meet
	- Goal test is a set of constraints specifying allowable combinations of variables for subsets of variables
- Example: Map Coloring
	![[Pasted image 20230301141807.png]]
	- Variables: Regions
	- Domain: Colors (3 different only)
	- Constraints: Adjacent regions must have different colors
	- Solutions are assignments satisfying all constraints
- Constraint Graphs
		![[Pasted image 20230301143301.png]]
	- Binary CSP - each constraints relates two variables
	- Binary constraint graph - nodes are variables, arcs are constraints
- Cryptarthmetic
		![[Pasted image 20230303140815.png]]
	- Example
		- W = 2
		- R = 6
		- T?, O?, F?, U?


##  <u>Varieties of CSPs and Constraints</u>
- Types of Constraints
	- Unary - restricts the value of single variable
	- Binary - relates two variables
	- Global Constraints - involves arbitrary number of variables
		- Between (x,y,z)
		- Alldiff(x,y,z)
	- Preferences (soft constraints)
- Varieties of CSPs
	- Discrete Variables
		- Finite domains
			- Size $d$ means $O(d^{n})$ complete assignments
		- Infinite domains (integers, strings, etc.)
			- E.g., job scheduling, variables are start/end times for each job need a constraint language, e.g., $StartJob_1$ + 5 ≤ $StartJob_3$
- Real-World CSPs	
	- Assignment problems 
		- e.g., who teaches what class 
	- Timetabling problems 
		- e.g., which class is offered when and where? 
	- Transportation scheduling 
	- Meeting Schedule


## <u>Solving CSPs</u>
- Standard search formulation of CSPs 
- States defined by the values assigned so far (partial assignments) 
	- Initial state: the empty assignment, {} 
	- Successor function: assign a value to an unassigned variable 
	- Goal test: the current assignment is complete and satisfies all constraints



## <u>Backtracking Search for CSP</u> 
- Basic uniformed algorithm for CSPs that
	1. One variable at a time
	2. Check constaints as you go
		- Incremental goal test
	- DFS with these two improvement is called backtracking search
- "Backtracks" when contraint is violated an reassigns variable at higher level so that lower level constraint can be satisfied.
		![[Pasted image 20230306140721.png]]
- Improvements to backtracking
	- Ordering
		- Which varialbe shoudl be assigned next
		- In what order should its values be tried
	- Filtering - Can we detect failure early?
	- Structure- Can we exploit the problem structure?
- Filtering - Ruling out assingments earlier on
	- Forward Checking
		- Keep track of domains for unassigned variables and cross off bad options
		- Cross off values that violate a constraint when added to the exisiting assignment
			- If adjacent neighbors are already assigned a color, don't have that color in the domain for that region
	- Arc Consistency
		- Direct constraints - two different contraints for undirected constraint
			- Both directions are checked, delete from the tail of the directed relationship
			- If we delete from the tail we have to recheck relationships.
		- Accounts for constraint not directly represented in constraint graph
		- Limitations
			- Runs inside of backtracking -> Slower
- Variable Ordering
	- Minimum Remaining Values - Variable Ordering
		- Choose the *variable* with the fewest values in its domain
	- Least Constraining Value - Value Ordering (within domain)
		- Choose the *value* in a selected variable that rules out the fewest values in domains of other variables
- K-Consistency
	- For each k nodes, any consistent assignment to k-1 can be extended to the $k$th node.
- Strong K-Consistency
	- Also consistent for k-1, k-2, ..., 1
	- Essentially ensuring at every step the problem is correct


## The Structure of Problems
- Problem Structure
	- Graph of $n$ variables can be broken into subproblems of only $c$ variables
- Tree-Structures CSPs
	- If the constraint graph has no loops, the CSP can be solved in $O(n \cdot d^{2})$ time
	- Algorithm
		- Order - Choose a root variable for the tree, order variables so that parents precede children
- Improving Structure
	- Cutset Conditioning
		- Instantiate (in all possible ways) the most constrained node(s) and remove it from the graph
			- The set of constrained nodes is called the *cutset*
		- Remove cooresponding assignment from domain of connected nodes
		- Use the rest of nodes to form a graph and then assign

## Local Search for CSP 
- Iterative Improvement
	- Uses a complete state that has violated constraints
	- It randomly targets violated constraints and fixes them until all are (hopefully) fixed
		- Variable selection: randomly selects a variable that is violating a constraint
		- Value selection: chooses the assignment that introduces the least amount of constraint violations going forward
