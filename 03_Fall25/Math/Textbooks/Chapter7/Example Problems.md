- 7.3✔️
- 7.4✔️
- 7.5✔️
- 7.6✔️
- 7.7❌
- 7.8❌

---
## Exercise 7.3

Consider whether the following statements are true or false:

- **(a)** The intersection of any two convex sets is convex.
	- True
		- If $A$ and $B$ are convex then for any two points $x,y\in A\cap B$ lie within both $A$ and $B$ $\therefore$ it also lies $A\cap B$
- **(b)** The union of any two convex sets is convex.
	- False
		- If we have two convex sets $A, B$ it is possible for there to be a gap between the two sets. If we have two points $x\in A$ and $y\in B$ then draw a line connecting these points then there will exist points on the line that $\notin A | B$ 
- **(c)** The difference of a convex set A from another convex set B is convex.
	- False
		- It is possible to have a convex set $A$ within another set $B$ and once we perform the operation $A/B$ this leaves holes within the remaining convex set.

---
## Exercise 7.4

Consider whether the following statements are true or false:

- a. The sum of any two convex functions is convex.
	- True
		- Assuming you have two convex functions $f$ and $g$, and a third $h=f+g$
		  To check for convexity of $h$ we can check that $h$ satisfies the convexity inequality.
			- $f=(\lambda x + (1-\lambda)y)$
			- $g=(\lambda x +(1-\lambda)y)$
			- $h=f+g=f(\lambda x + (1-\lambda)y)+g(\lambda x + (1-\lambda)y)=h(\lambda x + (1-\lambda)y)$
			  $h(\lambda x + (1-\lambda)y) \leq \lambda h(x) +(1-\lambda) h(y)$
			  Which shows that convexity is preserved through addition.
- b. The difference of any two convex functions is convex.
    - False
	    - If we have $f=x^2$ and $g=2x^2$ the result of $f-g$ is a concave function.
- c. The product of any two convex functions is convex.
	- False
		- If we have $f=x^2$ and $g=(x+1)$, the product results in a non-convex function.
- d. The maximum of any two convex functions is convex.
    - True
	    - The pointwise maximum of convex functions remains convex

---

## Exercise 7.5

Express the following optimization problem as a standard linear program in matrix notation:
$$\max_{x \in \mathbb{R}^2, \xi \in \mathbb{R}} p^T x + \xi$$
subject to the constraints that:
$$\xi \ge 0, x_0 \le 0 \text{ and } x_1 \le 3.$$

To express the above problem as a standard linear program we must define several variables that we will use in the derivation of the dual Lagrangian.

It is important to consider the formal definition of the Lagrangian provided from the textbook to help us define the linear program. The textbook states the Lagrangian as:
$$
\tag{7.40}
\mathcal{L}(x,\lambda)=c^Tx+\lambda^T(Ax-b)
$$
To properly express the optimization problem as a linear program we must be able to define the following:
- $x\to$ decision variable vector
- $c\to$ cost vector
- $A\to$ constraint matrix
- $b\to$ constraint vector

To begin, we can denote the vector of decision variables which is shown by the constrains as:
$$
x=
\begin{bmatrix}
x_0\\x_1\\\xi
\end{bmatrix}
$$
Furthermore, we can then define our cost vector as the coefficients applied to the decision variables from the vector $p$ within our problem statement. This results in:
$$
c=
\begin{bmatrix}
p_0\\p_1\\1
\end{bmatrix}
$$
Furthermore, we can construct our constraint matrix and vector by turning all of our constrains into the form $a_i^T x\leq b_i$ 
- $x_0 \le 0$
- $x_1 \le 3$
- $-\xi \le 0$
This gives us the following:
$$
\begin{matrix}
\begin{bmatrix}
1&0&0
\end{bmatrix}
\begin{bmatrix}
x_0\\x_1\\\xi
\end{bmatrix}\leq0
&&
\begin{bmatrix}
0&1&0
\end{bmatrix}
\begin{bmatrix}
x_0\\x_1\\\xi
\end{bmatrix}\leq3
&&
\begin{bmatrix}
0&1&-1
\end{bmatrix}
\begin{bmatrix}
x_0\\x_1\\\xi
\end{bmatrix}\leq0
\end{matrix}
$$
Resulting in:
$$
\begin{matrix}
A=\begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&-1
\end{bmatrix}
&&
b=\begin{bmatrix}
0\\3\\0
\end{bmatrix}
\end{matrix}
$$
Therefore, you know have all the elements needed to construct the Lagrangian and express the optimization problem as a linear program.

---
## Exercise 7.6

Consider the linear program illustrated in Figure 7.9:

$$\min_{x \in \mathbb{R}^2} -\begin{bmatrix} 5 \\ 3 \end{bmatrix}^{\top} \begin{bmatrix} x_1\\x_2 \end{bmatrix}$$

$$
\text{Subject to} \begin{bmatrix}
2 & 2 \\
2 & -4 \\
-2 & 1 \\
0 & -1 \\
0 & 1 \\
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
\leq
\begin{bmatrix}
33 \\
8 \\
5 \\
-1 \\
8
\end{bmatrix}
$$

Derive the dual linear program using Lagrange duality.

The first thing I would like to do is rewrite the problem to remove the negative sign in front of the cost vector, to do this we can rewrite the $\min$ problem as a $\max$ by doing the following:
$$
\min_{x \in \mathbb{R}^2} -\begin{bmatrix} 5 \\ 3 \end{bmatrix}^{\top} \begin{bmatrix} x_1\\x_2 \end{bmatrix}
\Longrightarrow
\max_{x \in \mathbb{R}^2} \begin{bmatrix} 5 \\ 3 \end{bmatrix}^{\top} \begin{bmatrix} x_1\\x_2 \end{bmatrix}
$$
We can also take it a step further, since these are not large matrices, to rewrite this as a linear equations:
$$
\begin{align}
\max_{x \in \mathbb{R}^2} 5x_1+3x_2 \\
s.t. Ax\leq b
\end{align}
$$

The next step in deriving the dual linear program is defining the variables we did in the prior problem so we can properly define our Lagrangian. This problem provides us with constraints that make this easy for us, by that I mean we are able to do following:
$$
x=\begin{bmatrix}
x_1\\x_2
\end{bmatrix},\;
c=\begin{bmatrix}
5\\3
\end{bmatrix},\;
A=
\begin{bmatrix}
2&2\\
2&-4\\
-2&1\\
0&-1\\
0&1
\end{bmatrix},\;
b=\begin{bmatrix}
33\\8\\5\\-1\\8
\end{bmatrix}
$$
Continuing the the derivation, I will next set up the Lagrangian w.r.t to both $x_1$ and $x_2$. Following the general formula for the Lagrangian from the textbook, for a maximization problem:
$$
\tag{7.40}
\mathcal{L}(x,\lambda)=c^\top x+\lambda^\top(b-Ax)
$$
We can plug in our values for $c, x^\top$ as well as the $5$ constraints defined to create the following Lagrangian:
$$
\begin{align}
\mathcal{L}(x_1,x_2,\lambda)= &\; c^\top x\\+&\;
\lambda_1\big(33-(2x_1+2x_2)\big)\\+&\;
\lambda_2\big(8-(2x_1-4x_2)\big)\\+&\;
\lambda_3\big(5-(-2x_1+x_2)\big)\\+&\;
\lambda_4\big(-1-(-1x_2)\big)\\+&\;
\lambda_5\big(8-(1x_2)\big)
\end{align}
$$
Finally to finish deriving the dual linear program using Lagrange duality you take the derivative of $\mathcal{L}(x_1,x_2,\lambda)$ w.r.t to both $x_1$ and $x_2$ providing you with the Lagrange duality.
$$
\begin{align}
\tag{D1}
\frac{d\mathcal{L}}{dx_1}\Rightarrow&\;
5-2\lambda_1-2\lambda_2+2\lambda_3=0\\\\
\tag{D2}
\frac{d\mathcal{L}}{dx_2}\Rightarrow&\;
3-2\lambda_1 +4\lambda_2-\lambda_3+\lambda_4-\lambda_5=0
\end{align}
$$

---

## Exercise 7.7

Consider the quadratic program illustrated in Figure 7.4:

$$\min_{x\in \mathbb{R}^{2}} \frac{1}{2} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix}^{\top} \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix} + \begin{bmatrix} 5 \\ 3 \end{bmatrix}^{\top} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix}$$

$$\text{Subject to}
\begin{bmatrix}
1 & 0 \\
-1 & 0 \\
0 & 1 \\
0 & -1 
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} 
\end{bmatrix} \le \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}$$

Derive the dual quadratic program using Lagrange duality.

---

## Exercise 7.8

Consider the following convex optimization problem:

$$\min_{w\in\mathbb{R}^{D}} \frac{1}{2} w^{\top} w$$

subject to $w^{\top} x \ge 1$.

Derive the Lagrangian dual by introducing the Lagrange multiplier $\lambda$.