## Preorder Processing
```
In-Order: ((2+2)*((1*3)/2))
Pre-Order: (* (+ 2 2) (/ (* 1 3) 2))
```

## Setq
- Sets a global variable
```
> (setq x 4)     # x is now 4
> (+ x 3)        # x is now 7

```
- Not allowed to use global variables for the course
	- Need to focus on recursion

## Relational Operators
```
> (> 4 3)
> t
> (> 3 4)
> nil          # false
```

## Logical Operators
- and, or, not
```
> (and ((> 4 2) (< 4 1)))    # result will be an error, no operator in the brackets
> error
> (and (> 4 2) (< 4 1))      # correct way to write
> nil
```

## Functions
```
;cube of a and b and add them

(defun sum_cube(a b)
	(+ (* a a a) (* b b b))
)

(sum_cube 3 4 5)    # calls function
```

## Control Structures
- Conditionals $\rightarrow$ <u>cond</u>
	- Cannot executre multiple statements after a condition is satisfied
	```
	(setq x 4)
	(cond ((< x 2) (+ x 1))
		  ((= x 2) (* x 5))
		  (t x)
	)
	```

## Data Types
- Atom
	- Number
	- Symbol
		- Can be string too
- List
	- Can have differing types
	- Nestable

## List
```
> (setq x '(4 ab))    # need the ' symbol to denote list
```
- Not an object

## Temporary Variables (for functions)
- Keyword: `let`
- Designed to assign multiple variables at a time
```
(defun prand (x)
	(
		let (
			(r (random x))
		)
	)
	(
		cond (
			(< r (/ x 2))
			(t (* r r))
		)
	)
)
```

## Property List - setf
- Paired with get
```
(setf (get 'symbol 'property) value)
```

```
(setf (get 'mary 'hair) 'brown)
> (get 'mary 'hair)
> brown
```

```
(setf (get 'carol 'children) '(Paul Martha))
> (get 'carol 'children)
> (Paul Martha)
```