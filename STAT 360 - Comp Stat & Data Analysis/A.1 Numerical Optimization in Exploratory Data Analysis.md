## Functions in R
```r
function_name <- function(argument) { 
	# function body 
}
```
Example:
	![[Pasted image 20230926071859.png | 200]]
```r
fahrenheit_to_Celsius <- function(temp_F = 0) { 
	temp_C <- (temp_F - 32) * 5/9 
	return(temp_C) 
}
```
- Can pass multiple args individually or pass in an "array" (c())

## Numerical Optimization in R
- Numerical Optimization - selection of the best element or set of elements against some criteria
- One example is optimizing *skewness* -- so that it is minimized
```r
poweredSkewness <- function(power = 1) { 
	transformedValues <- (MG[,2]) ^ power 
	resultingSkewness <- abs(skewness(transformedValues)) 
	return(resultingSkewness) 
}
```
- Particle Swarm Optimization
	- Random values are picked - 'particles'
	- Move around the search space and swarm towards the optimal solution
	- Represented as `psoptim()` in R from the `pso` package
```r
psoptim(par = c(1), fn = poweredSkewness, lower = -9e9, upper = 9e9
```
- Args
	- Why in this example is par = c(1)? If just an init value?
- Output
	- $par - optimal solution
	- $value - the optimal result of the function
	- $counts - steps the algo took
	- $convergence/ $message - indicate success/failure

## Optimization for Simple Linear Regression
Sum of Squared Residuals
$$ SSR = \sum_{i=1}^{n}(y_i-f(x_i))^2  $$
Best Slope
$$b_1 = r \frac{s_y}{s_x}$$
$$ b_0 = y - b_1 \bar{x} $$
Particle Swarm