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
0&0&-1
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
Therefore, you know have all the elements needed to construct the Lagrangian and express the optimization problem as a linear program. The optimization problem expressed as a standard linear program is shown as follows: 

$$
\begin{align}
\max_{\lambda\in\mathbb{R}^m}&\; -
\begin{bmatrix}
0&3&0
\end{bmatrix}
\begin{bmatrix}
\lambda_0\\
\lambda_1\\
\lambda_2
\end{bmatrix}\\
\text{subject to }&\;
\begin{bmatrix}
p_0\\p_1\\1
\end{bmatrix}+
\begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&-1
\end{bmatrix}
\begin{bmatrix}
\lambda_0\\
\lambda_1\\
\lambda_2
\end{bmatrix}=0\\
&\; \lambda\geq0
\end{align}
$$

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

The textbook provides a definition for the Lagrangian which is written as follows:
$$
\tag{7.40}
\begin{align}
\mathcal{L}(x,\lambda)=c^\top x +\lambda^\top (Ax-b)
\end{align}
$$
Furthermore, it then goes on to provide a formal definition for the derivative of the $\mathcal{L}(x,\lambda)$ w.r.t $x$ which is defined as follows:
$$
\tag{7.42}
c+A^\top\lambda = 0
$$
Therefore, rewrite the above equation to define our dual Lagrangian as follows:
$$
\mathcal{D}(\lambda)=-\lambda^\top b
$$
The textbook states that the goal within the Dual Lagrangian is to maximize the $D(\lambda)$ w.r.t the constrains provided in the equation, therefore it defines the dual Lagrangian as Linear program as follows:
$$
\tag{7.43}
\begin{align}
\max_{\lambda\in\mathbb{R}^m}&\; -b^\top\lambda\\
\text{subject to }&\; c+A^\top \lambda=0\\
&\; \lambda \geq 0
\end{align}
$$
Defining our terms from the problem statement we get the following
$$
\begin{align}
b^\top =&\;
\begin{bmatrix}
33 \\
8 \\
5 \\
-1 \\
8
\end{bmatrix}\\\\
c =&\;
\begin{bmatrix}
-5 \\
-3
\end{bmatrix}\\\\
A= &\;
\begin{bmatrix}
2 & 2 \\
2 & -4 \\
-2 & 1 \\
0 & -1 \\
0 & 1 \\
\end{bmatrix}
\end{align}
$$
and finally we can define our dual Lagrangian linear program:
$$
\begin{align}
\max_{\lambda\in\mathbb{R}^m}&\; 
-\begin{bmatrix}
33 &
8 &
5 &
-1 &
8
\end{bmatrix}
\begin{bmatrix}
\lambda_0 \\
\lambda_1 \\
\lambda_2 \\
\lambda_3 \\
\lambda_4
\end{bmatrix}\\
\text{subject to }&\; 
\begin{bmatrix}
-5 \\
-3
\end{bmatrix}+
\begin{bmatrix}
2&2&-2&0&0\\
2&-4&1&-1&1
\end{bmatrix} 
\begin{bmatrix}
\lambda_0 \\
\lambda_1 \\
\lambda_2 \\
\lambda_3 \\
\lambda_4
\end{bmatrix}=0\\
&\; \lambda \geq 0
\end{align}$$

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

![[Pasted image 20251115132615.png]]
The textbook provides an illustration of exercise 7.7 as shown above. In the figure we can see a darkened gray box which indicates where are constraints are being placed within the quadratic program. Furthermore, this allows us to infer that visually the minimization will occur within this gray box.

The textbook defines a convex quadratic object function, where the constraints are affine. as follows:
$$
\begin{align}\tag{7.45}
\min_{x\in\mathbb{R}^d}&\; \frac{1}{2}x^\top Q x +c^\top x \\
\text{subject to }&\; Ax\leq b
\end{align}
$$
Furthermore, it goes on to define the elements of this function as follows:
- $A\in \mathbb{R}^{m\times d}$
- $b\in \mathbb{R}^m$
- $c\in \mathbb{R}^d$
- $Q\in \mathbb{R}^{d\times d}$
	- Where $Q$ is a square symmetric matrix that is positive definite making the objective function convex
- $d$ is the # of variables
- $m$ is the # linear constraints

The textbook then goes on to define the Lagrangian for a Quadratic program as follows:
$$
\begin{align}
\tag{7.48a}
\mathcal{L}(x,\lambda)=&\; \frac{1}{2} x^\top Qx + c^\top x+\lambda^\top(Ax-b)
\\\\
\tag{7.48b}
=&\;
\frac{1}{2} x^\top Qx + (c + A^\top \lambda)^\top x -\lambda^\top b
\end{align}
$$
Then, the textbook provides us with formal definitions for the derivative of $\mathcal{L}(x,\lambda)$ w.r.t $x$:
$$
\tag{7.49}
Qx+(c+A^\top \lambda)=0
$$
Solving for x we get:
$$
\tag{7.50}
x=-Q^{-1} (c+A^\top \lambda)
$$
Substituting the equation we get for $x$ into $\mathcal{L}(x,\lambda)$ provides us with the formal definition of the Dual Lagrangian of a Quadratic Function:
$$
\tag{7.51}
\mathcal{D}(\lambda)=-\frac{1}{2}(c+A^\top\lambda)^\top Q^{-1}(c+A^\top \lambda)-\lambda^\top b
$$
Finally, the textbook defines the dual optimization problem of a quadratic function as follows:
$$
\tag{7.52}
\begin{align}
\max_{\lambda\in\mathbb{R}^m}&\; -\frac{1}{2} (c+A^\top\lambda)^\top Q^{-1} (c+A^\top\lambda) -\lambda^\top b\\
\text{subject to }&\; \lambda\geq 0
\end{align}
$$
Defining our terms from the problem statement we get the following:
- $Q\Longrightarrow \begin{bmatrix}2&1\\1&4\end{bmatrix}$
- $c\Longrightarrow \begin{bmatrix}5\\3\end{bmatrix}$
- $A\Longrightarrow \begin{bmatrix}1 & 0 \\1 & 0 \\0 & 1 \\0 & -1\end{bmatrix}$
- $b\Longrightarrow \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}$
Solving for the unknows we get:
$$
\begin{align}
A^\top\lambda=&\; 
\begin{bmatrix}
1&1&0&0\\
0&0&1&-1
\end{bmatrix}
\begin{bmatrix}
\lambda_0\\
\lambda_1\\
\lambda_2\\
\lambda_3
\end{bmatrix}
\\
=&\;
\begin{bmatrix}
\lambda_0 + \lambda_1 \\
\lambda_2 - \lambda_3
\end{bmatrix}
\end{align}
$$
$$
\begin{align}
Q^{-1}=&\;
\begin{bmatrix}
\frac{4}{7}&-\frac{1}{7} \\
-\frac{1}{7}&\frac{2}{7}
\end{bmatrix}
\end{align}
$$

Now plugging into equation $7.51$ for the Dual Lagrangian of a Quadratic Function we get:
$$
\mathcal{D}(\lambda)=-\frac{1}{2}
\left(
\begin{bmatrix}5\\3\end{bmatrix}
+\begin{bmatrix}
\lambda_0 + \lambda_1 \\
\lambda_2 - \lambda_3
\end{bmatrix}
\right)^\top 
\begin{bmatrix}
\frac{4}{7}&-\frac{1}{7} \\
-\frac{1}{7}&\frac{2}{7}
\end{bmatrix}
\left(
\begin{bmatrix}5\\3\end{bmatrix}
+\begin{bmatrix}
\lambda_0 + \lambda_1 \\
\lambda_2 - \lambda_3
\end{bmatrix}
\right)-
\begin{bmatrix}
\lambda_0&
\lambda_1&
\lambda_2&
\lambda_3
\end{bmatrix}
\begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}
$$
Finally the dual quadratic program using Lagrange duality can be expressed as the following:
$$
\begin{align}
\max_{\lambda\in\mathbb{R}^m}&\; -\frac{1}{2}
\left(
\begin{bmatrix}5\\3\end{bmatrix}
+\begin{bmatrix}
\lambda_0 + \lambda_1 \\
\lambda_2 - \lambda_3
\end{bmatrix}
\right)^\top 
\begin{bmatrix}
\frac{4}{7}&-\frac{1}{7} \\
-\frac{1}{7}&\frac{2}{7}
\end{bmatrix}
\left(
\begin{bmatrix}5\\3\end{bmatrix}
+\begin{bmatrix}
\lambda_0 + \lambda_1 \\
\lambda_2 - \lambda_3
\end{bmatrix}
\right)-
\begin{bmatrix}
\lambda_0&
\lambda_1&
\lambda_2&
\lambda_3
\end{bmatrix}
\begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}\\
\text{subject to }&\; \lambda\geq 0
\end{align}$$


---

## Exercise 7.8

Consider the following convex optimization problem:

$$
\begin{align}
\min_{w\in\mathbb{R}^{D}}&\; \frac{1}{2} w^{\top} w\\
\text{subject to}&\; w^{\top} x \ge 1
\end{align}
$$

Derive the Lagrangian dual by introducing the Lagrange multiplier $\lambda$.

To begin, the textbook states that "the idea of a Lagrange multiplier is to **replace** the step function with a linear function." Our current primal function is shown above in the problem as the function we are trying to minimize.  The textbook then defines the Lagrangian by introducing the Lagrange multipliers $\lambda_i \geq 0$ corresponding to each inequality constraint respectively s.t:
$$
\begin{align}
\tag{7.20a}
\mathcal{L}(x,\lambda) =&\; f(x)+\sum_{i=1}^m\lambda_ig_i(x)
\\
\tag{7.20b}
&\; = f(x) + \lambda^\top g(x)
\end{align}
$$
The textbook then goes on to state the formal definition of the *primal problem* as well as the associated *Lagrangian dual problem*. For conciseness I will state that the primal problem is our $\min$ optimization problem stated above and the *Lagrangian dual problem* definition is as follows:
$$
\tag{7.22}
\begin{align}
\max_{\lambda\in\mathbb{R}^m}&\; \mathcal{D}(\lambda)\\
\text{Subject to }&\; \lambda \geq 0,
\end{align}
$$
where $\lambda$ are the dual variables and $\mathcal{D}(\lambda)=\min_{x\in\mathbb{R}^d}\mathcal{L}(x,\lambda)$.

Now that we have properly defines we can start deriving our terms. To begin, we first need to solve for our step function which is done simply by doing the following:
$$
\begin{align}
\text{Constraint:} &\;\; w^{\top} x \ge 1\\
\text{Rewrite:} &\;\; 1- w^{\top} x \le 0\\\therefore\\
g(w)=&\; 1- w^{\top} x
\end{align}
$$
Furthermore, we already have $f(x)$ defined from the problem statement and $\lambda$ are the dual variables therefore we can now create are Lagrangian as follows;
$$
\begin{align}
\mathcal{L}(w,\lambda)= &\; f(w) + \lambda^\top g(w)\\
=&\; \left(\frac{1}{2} w^{\top} w\right) + \lambda^\top \left(1- w^{\top} x\right)
\end{align}
$$
The dual function can now be found by doing the following:
$$
\begin{align}
\mathcal{D}(\lambda)=&\; \min_{w\in\mathbb{R}^d}\mathcal{L}(w,\lambda)\\
=&\; \min_{w\in\mathbb{R}^d} \left(\frac{1}{2} w^{\top} w\right) + \lambda^\top \left(1- w^{\top} x\right)\\
=&\; \min_{w\in\mathbb{R}^d} \frac{1}{2} w^{\top} w - w^{\top} x\lambda^\top + \lambda^\top\\
\end{align}
$$
It is important to note that the constraint $w^{\top} x \ge 1$ defines our dot product of $w$ and $x$ meaning that we know both $w,x\in\mathbb{R}^D$ with that being said we know that $g(w)$ is then just a scalar value as well as $\lambda$ (single $\lambda$ value). We can now continue solving the dual function by minimizing the Lagrangian, to do this we will take the derivative of $\mathcal{L}(x,\lambda)$ w.r.t $w$:
$$
\begin{align}
\nabla_w\mathcal{D}(\lambda) =&\; \min_{w\in\mathbb{R}^d} \frac{1}{2} w^{\top} w - w^{\top} x\lambda^\top + \lambda^\top\\
=&\; w-x\lambda
\end{align}
$$
Setting that equal to zero and solving for $w$ we get:
$$
\begin{align}
w-x\lambda =&\; 0\\
w=x\lambda
\end{align}
$$
Plugging back in to $\mathcal{D}(\lambda)$ for w we get:
$$
\begin{align}
\mathcal{D}(\lambda) =&\; 
\frac{1}{2} w^{\top} w - w^{\top} x\lambda^\top + \lambda^\top \\
=&\;
\frac{1}{2} \lambda^2 x^\top x-\lambda^2 x^\top x+\lambda \\
=&\;
-\frac{1}{2} \lambda^2 x^\top x + \lambda
\end{align}
$$
Finally, we are able to derive the Lagrangian dual by maximizing $\mathcal{D}(\lambda)$:
$$
\max_{\lambda\geq0}
-\frac{1}{2} \lambda^2 x^\top x + \lambda
$$
