## Server-side JavaScript
- Node.js
	- Standalone interpreter for JavaScript
		- Uses Google's V8 JavaScript engine
	- Extends JS
		- Adds support for file I/O, networking, etc.

## Modules
- JS initially designed for browser
	- Limited feature set (intentional) for security purposes
		- Ex: No access to file system, can't run external programs, ...
- Built-in modules bring full feature set of most programming languages to JS
	- **fs**: access to file system
	- **readline**: user input from command line
	- **http**: create an HTTP server
	- **child_process** run external programs
- External modules obtained using NPM
	- `npm install package`
	- List of external modules stored in 'package.json' file
		- Allows other to easily install all dependencies 
			- Install all at once using `npm install`
- Imported with key-function `require`
	![[Pasted image 20231002123053.png | 450]]
	- Set package to a var
	- JS workflow (.js)
- Module workflow (.mjs)
	- Can use import statements
```js
import * as fs from 'node:fs';
// OR
import { readFile } from 'node:fs';
```


