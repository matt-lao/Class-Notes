## Agents and Environments

![[Pasted image 20230210135902.png]]
An agent is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through actuators.

- Percept and percept sequence
	- Percepts are the inputs at given moment
	- Percept sequence is the history of inputs
		- Useful for learning based on past inputs
- Agent Behavior
	- Function
		- Maps from percept history to actions $[f: P* → A]$
	- Program
		- Runs physical architechture to produce $f$
		- agent = architechture + program
			- architechture
				- computing device, physical sensors, and actuators
			- program
				- maps percepts to actions
	- Function is theory, Program is application

## Rationality
- Agent should strive to "do the right thing"
	- Performance measure
		- Decided by designer
		- Specific criteria for success of agent's behavior
- Performance measure, Environment, Actuators, Sensors (PEAS)
	- First start with the task environment
	- Performance measure can be based on several critera
		- The balance of which measures carry more weight is also important

## Nature of Environments
- Types
	- Observability
		- Fully observable
		- Partially
		- Unobservable
	- Time constraint
		- Static - does not change while deciding
		- Dynamic - changes regardless of agent
		- Semi-dynamic - environment hangs but the quickness of decision affects performance measure
	- Environmental Representation
		- Discrete - represented by individual atomic items (8x8, 2x4)
		- Continuous - subdivided infinitely
	- Consequences
		- Episodic - decisions only affect a certain time frame
		- Sequential - lasting consequences
	 - Predictability
		 - Deterministic - action in the same state will result in the same outcome
		 - Stochastic - changes randomly
	 - Knowledge
		 - Known - Model governing the environment is fully understood
			 - We know what happens if we perform some action in some state
		 - Unknown - Model of environment not entirely known
			 - Agent explores and learns from the environment is a rational way
	- Other Agents
		- Entities within the environment
		- Single/multi
		- Competitive/Cooperative
		- Communication
## Agent Types
- Simple reflex agents
	- Does an action when the current conditions percieved match conditions of a defined rule.
	- Conditonal logic (if/elif/else)
		![[Pasted image 20230219172931.png]]
- Model-based reflex agents
	- Incorperates transition and sensor models
		- Transition model - knowledge about how the world works
		- Sensor model - knowledge of how the an agent's precepts descibe the current state of the world
			- Red light on car in front of us means it is braking
		![[Pasted image 20230219173818.png]]
- Goal-based agents
	- More flexible than models because the goal can be dynamic or changed base on the situation
	![[Pasted image 20230219173910.png]]
- Utility-based agents
	- Represents choices on a spectrum rather than binary distinction
	![[Pasted image 20230219173934.png]]
- Learning agents
	![[Pasted image 20230219174020.png]]
- State and transition representation
	- Atomic
		- Each state is indivisible; no internal or deeper structure
	- Factored
		- States have variables and attributes
	- Structured
		- States have relationships to each other