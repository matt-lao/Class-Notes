## Structure
```
; takes a list and counts the top level elements in the list
(defun length (lst)
	(cond ((null lst) 0)
		  (T (+ 1 (length (cdr list)))
	)
)
```

## Functions
- car - gives first element of list
- cdr - gives everything but first element
- cddr - (cdr (cdr x))
	- inner most statement executes first
- listp - returns boolean if list or not
- atom - returns boolean if atom or not
- numberp - return boolean if number or not
- append - appends to end of the list
	- can append an entire list
	- does not mutate variable - need to update or create new variable to store
- cons - adds to front of list
	- only can add on atom
	- does not mutate variable - need to update or create new variable to store
- equals
	- equal
		- equal content
	- eq
		- equal reference
- member - returns boolean if element is a member of a list or not
- reverse - reverses a list
	- does not mutate variable
- mapcar - applies given operation to list or lists
	```
	> (mapcar '* '(2 3 4) '(1 2 3))
	> (2 6 12)
    ```
	```
	> (mapcar '2- '(5 4 3))
	> (3 2 1)
    ```
	```
	; this function determines if an element is less than 2
	(defun less2 (x)
		(< x 2)
	)

	> (mapcar 'less2 '(3 4 5 1))
	> (() () () T)
	; () signifies nil
	
    ```

## Example
```
; stored in database as 'year' and 'kind'
(defun retrieve_cars (database yr model)
	(cond 
		; if nothing in database -> empty list
		((null database)())
		; 'if case'
		((and (equal (get (car database)) 'year yr)) 
			  (equal (get (car database)) 'kind model)
			  (cons (car database) 
				  (retrieve_cars (cdr database yr model))
			  )
		))
		; 'else case'
		(t (retieve_cars (cdr database yr model)))
	)
)
```