- 7.3✔️
- 7.4❌
- 7.5❌
- 7.6❌
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
	- If $f$ and $g$ are convex, then
- b. The difference of any two convex functions is convex.
    
- c. The product of any two convex functions is convex.
    
- d. The maximum of any two convex functions is convex.
    

---

## Exercise 7.5

Express the following optimization problem as a standard linear program in matrix notation:

$$\max_{x \in \mathbb{R}, \xi \in \mathbb{R}} \xi x + p$$

subject to the constraints that:

$$\xi \ge 0, x_0 \le 0 \text{ and } x_1 \le 3.$$

---

## Exercise 7.6

Consider the linear program illustrated in Figure 7.9:

$$\min_{x \in \mathbb{R}^2} \begin{bmatrix} 2 \\ 1 \end{bmatrix}^{\top} x$$

subject to:

$$\begin{bmatrix} 1 & -2 \\ -1 & 1 \end{bmatrix} x \le \begin{bmatrix} 5 \\ 8 \end{bmatrix}, \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} x \ge \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$

Derive the dual linear program using Lagrange duality.

---

## Exercise 7.7

Consider the quadratic program illustrated in Figure 7.4:

$$\min_{x\in \mathbb{R}^{2}} \frac{1}{2} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix}^{\top} \begin{bmatrix} 2 & 1 \\ 1 & 4 \end{bmatrix} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix} + \begin{bmatrix} 5 \\ 3 \end{bmatrix}^{\top} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix}$$

$$subject~t_{o} \begin{bmatrix} 1 & 0 \\ -1 & 0 \\ 0 & 1 \\ 0 & -1 \end{bmatrix} \begin{bmatrix} x_{1} \\ x_{2} \end{bmatrix} \le \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}$$

Derive the dual quadratic program using Lagrange duality.

---

## Exercise 7.8

Consider the following convex optimization problem13:

$$\min_{w\in\mathbb{R}^{D}} \frac{1}{2} w^{\top} w$$

subject to $w^{\top} x \ge 1$.

Derive the Lagrangian dual by introducing the Lagrange multiplier $\lambda$.