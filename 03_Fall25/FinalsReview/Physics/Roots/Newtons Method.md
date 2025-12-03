The Newton-Raphson method is an iterative numerical technique to find roots of a real-valued function. It accomplishes by using the derivative of the function to converge rapidly to the root.

**Steps:**
1) Evaluate $f^\prime (x)$
2) Create an initial guess of the root $(x_i)$ and use this to estimate the new value of the root $(x_{i+1})$
$$
x_{i+1} = x_i - \frac{f(x_i)}{f^\prime (x_i)}
$$
3) Find the absolute relative approximation error $|\in_a|$:
$$
|\in_a| = \left| \frac{x_{i+1} - x_i}{x_{i+1}} \right| \times 100
$$
4) Compare the $\in_a$ with $\in_s$
	- $\in_a\to$ Relative Approximation Error
	- $\in_s\to$ Pre-defined Relative Error Tolerance
5) Repeat until the error falls within a specific range of the tolerance.