- Every HTML element represented as an object within the document
	![[Pasted image 20231002103440.png]]
	- Can use JavaScript to manipulate the DOM
- Retrieving HTML Elements
	- global object `document`
	- Access by tag
		- `document.getElementsByTagName(tag)`
		- returns array
	- Access by class
		- `document.getElementByClassName(class)`
		- returns array
	- Access by id
		- `document.getElementById(class)`
		- returns single element
- Modifying HTML Elements
	- Image's **src** attribute can be changed to modify image shown
	- Any element's **style** attributer to changer color, size, etc.
		![[Pasted image 20231002103823.png | 500]]
- Adding HTML Elements
	- Two steps
		- Create new element
		- Append it as a child of an existing HTML element
		![[Pasted image 20231002103923.png | 500]]
			- create new paragraph + append to container1

## In-Class
- How does JS work?
	- Visit site w/ JS
	- Browser read line-by-line
		- Executes each line as it reads it
			- If browser cannot understand a line -> stops running that code and creates an error message
	- Can view JS output in console -> chrome dev tools

## JavaScript Overview
- Script Tag
	- To include JS in HTML, use the `<script>` tag
		- Code goes inside, not content
		- Can also link to external files w/ code
```html
<script type="application/javascript">
  // code goes here!
</script>
<script type="application/javascript" src="file.js"></script>
```
	- Can go in head or body - leads to differing behavior
		- Head - Loads before any HTML element in body
		- Body - Loads after elements declared prior to the script tag
- Comments
	- Uses C-style commenting
		- `//` - single line comment
		- `/*  */` - multi line comment
- Output
	- Print to developer console - `console.log("message");`
	- Show message in pop-up window - `alert("message");`
- Variables
	- Similar to Python, Java, C/C++
	- Variables are dynamically types
		- In uninitialized -> undefined
	- Use keyword **var** or **let** to declare new var
	- Any combination of letters, numbers, $, and _
		- Cannot start w number
- Data types
	- Undefined (uninitialized) - `var my_variable;`
	- Null (explicitly empty) - `var my_variable = null;`
	- Boolean (T or F) - `var my_variable = true;`
	- Number (Integer/Floating Point) - `var my_variable = 3.14;`
	- String (single or double quotes) - `var my_variable = "hello";`
- Variable Data Types
	- Array - `var my_variable = [1, 2.5, "hi"];`
	- Object - `var my_variable = {id: 1, amount: 2.5, phrase: "hi"};`
	- Function - `var my_variable = function () {console.log('hi');};`
- Functions
	- Similar to other languages (Python, Java, C/C++)
		- All parameters are optional
			- Unused will be undef
		- Variable scopes
			- Variables declared with **var** are scoped to the function
			- Variables declared with **let** are scoped to a block (curly braces)
			- Can be declared anywhere
				- If inside another function, it can only be called within that function
- Boolean Comparisons
	- Mostly like other langs
	- Extra operators
		- === - same value and type
		- !== - not same value or not same type