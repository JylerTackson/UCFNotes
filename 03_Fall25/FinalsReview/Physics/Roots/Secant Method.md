The Secant method is a numerical method to find roots of a real valued function. This method does NOT require the derivative of a function making it more robust than newtons method however it converges slower. Secant utilizes an approximation of the derivative and plugs this into the newtons Rapson method to create the formula:
$$
x_{i+1} = x_i - \frac{f(x_i)(x_i-x_{i-1})}{f(x_i)-f(x_{x-1})}
$$
**Steps:**
1) Calculate the next estimate of the root from two initial guesses:
$$
x_{i+1} = x_i - \frac{f(x_i)(x_i-x_{i-1})}{f(x_i)-f(x_{x-1})}
$$
2) Find the absolute relative approximation error $|\in_a|$:
$$
|\in_a| = \left| \frac{x_{i+1} - x_i}{x_{i+1}} \right| \times 100
$$
3) Compare the $\in_a$ with $\in_s$
	- $\in_a\to$ Relative Approximation Error
	- $\in_s\to$ Pre-defined Relative Error Tolerance
4) Repeat until the error falls within a specific range of the tolerance.
$$$$