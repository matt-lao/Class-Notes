## Elements

##### Paragraphs
`<p>`
- Spacing for humans
- Text spaces are condensed

##### Headings
`<h>`

##### Formatting
`<b> <i>`


## CSS
- Style Rules
	- Selector
	- Property-value pairs
		![[Pasted image 20230911123025.png]]
- Connecting CSS with HTML
	- Inline
		- Put as an attribute of element (style)
		- Applies only to specific element
		- Highest priority -- overrides headers
	- Embedded
		- Put in the header
		- Applies to all elements on the specific page
	- External
		- Referencing an external file -- linked in the head
		- Can be applied to multiple pages
- Colors
	- RGB -- based on receptors in the eye
	- Hex
		- Red - first two digits, Green - first two digits, Blue - last two digits
	- RGBA
		- a - alpha 
			- Transparency
			- Floating point between 0 - 1 
				- 0 being fully transparent
				- 1 being fully opaque
	- HSL
- Fonts
	- 'font-family' selects the font that is used for text
		- Can list backups if user does not have specific one installed
			- Always use:
				- San-serif or Serif -- call default fonts
		- Must use quotes if the font names have spaces
	```css
	h1 {
		font-family: "Times New Roman";
	}

	h3 {
		font-family: Arial, san-serif;
	}
	
```
	- 'font-size'
		- Pixels (px)
			- Not good for mobile devices -- have more pixels than a desktop screen
		- Ems (em)
			- Scalable unit: ratio compared to the parent size
		- Rems (rem)
			- Scalable unit: ration compared to the root (html) size
		- Best practice - Use percentage for the html element, use rems for everything else
			- Allows content to scale well on mobile devices
	- 'font-style' - toggles italics on and off
	- 'font-weight' - toggles bold
	- Shorthand
		```css
		p {
			font-family: Arial;
			font-size: 1rem;
			font-style: italic;
			font-weight: bold;
		}
		/*OR*/
		p {
			/*style weight size family*/
			font: italic bold 1rem Arial;
		}
```
- Selectors
	- Position - changes style based on position of element
	```css
	p a {
		color: rgb(35,70,200);
	}
```
			- just styles anchor tags in paragraphs
	- Psuedo-classes - changes style based on state
		```css
		a:link { color: 2346C8; }      /* unvisited link */
		a:visited { color: #A81CA5; }  /* visited link */
		a:hover { color: #7C7EEF; }    /* moused over */
		a:focus { color: #7C7EEF; }    /* selected with keyboard */
		a:active { color: #FF1A1A; }   /* activated link */
```

- Priority
	- in-Line
		- id
			- class
				- elements*
					- * most to least specific

## Box Model
![[Pasted image 20230913135329.png | 300]]
- Padding
	- Inside border
	- Background color applies
- Margin
	- Outside border
	- Transparent always

Padding
```css
#paddedbox {
  padding: 10px 5px 3px 8px; /* top, right, bottom, left */
  padding: 8px 12px;         /* vertical, horizontal */
  padding: 10px;             /* all sides */
}
```

Border
```css
#borderbox {
  border: 1px dotted #000000; /* black dotted line 1px thick */
  border-top: 3px solid red;  /* red top as solid line 3px thick */
}
/* Must order like this otherwise the most bottom thing will overrite*/
```

