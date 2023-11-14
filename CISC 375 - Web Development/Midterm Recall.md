## HTML
- Elements
	- HTML - wraps all content in an HTML file
	- Head - info about page - page title (top of the tab in browser)
		- Also includes meta tags
	- Body - wraps the content on the page
	- Paragraph
- Tag - markers for beginning/end of element
	- Some elements have opening and closing tag in one tag
- Attributes - name-value pair that exists within a start-tag
	```html 
	<img src="lovelace.jpg" alt="Ada Lovelace" />
	```
	- Provides extra information about the data in the tag

## CSS
- Foundations
- All CSS typically uses a grid based system

## Static Servers
- Route points to content that is sent to client and rendered on their end

## Dynamic Servers
- Files are generated on the server side
- Usually by using html templates and javascript
- 

## JavaScript
- DOM
- Module-based vs. Traditional
	- Import vs. Require statements
		- Traditional java script uses require statements
		- Module-based js uses imports statements
	- File extension
		- Traditional - .js
		- Module based - .mjs
	- Functionality
		- Traditional javascript was designed for simple brower based functions
		- Module based javascript expands the functionality of traditional to add this like the ability to have file i/o and such
- Callbacks
	- Function notation
		- Declare a function names and save the function to it
	- Anonymous 
		- Just a singular callback for the scope of the current function
		- Arrow notation
- Promises
	- Can turn callbacks into objects that resolve/reject when user either
		- Implicitly calls for promise to be returned
		- Explicitly call resolve()/reject() and passes what should be returned upon resolving/rejecting
			- Rejecting will account for the case where there is an error
	- Good use cases
		- Multiple asynchronous events that we need to have finish before moving on
			- Downloading 5 different files but need them to finish before moving ahead with a query based on the content of those files
		- Sequential events
			- Downloading a file and based on the contents of that file I will then download another file