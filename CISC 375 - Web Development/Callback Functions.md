## Overview
- Callback functions are setup to be called at a later time
	- Other code will later "call back"
	- Serves as a hook for custom functionality when some event occurs
- User Event Callbacks
	- Callbacks can be attached to HTML element for various user interaction events
		- Click, keypress, etc.
	- Two ways to attach
		- HTML attributes
			- Add attribute "on____"
				- Value will be JS executed when the event occurs
					![[Pasted image 20231002114117.png]]
		- JS event listener
			- Use `addEventListener()` method for an HTML object
				![[Pasted image 20231002114155.png]]
- Functions as arguments
	- Multiple ways to pass a function as an argument to another
		- Using a previously defined function's name
			![[Pasted image 20231002114511.png | 500]]
		- Using a variable that stores the function
			![[Pasted image 20231002114532.png | 500]]
		- Define a new anonymous function inline
			![[Pasted image 20231002114550.png | 500]]
		- Define a new anonymous function using short-hand (arrow notation)
			![[Pasted image 20231002114607.png | 500]]
- Not just user events
	- Example - custom functionality when sorting -> similar to comparator in Java or lambda in Python
		- Pass in callback to a function for custom comparison
			![[Pasted image 20231002114923.png]]
- Getting Data from the Web
	- Download content from specified web address
	- `XMLHttpRequest()`
		![[Pasted image 20231002121956.png |500]]
		- ReadyState
			- 0 - request not initialized
			- 1 - server connection established
			- 2 - request received
			- 3 - processing request
			- 4 - request finished and response is ready
		- Status
			- 200 - OK
			- 404 - Not found
