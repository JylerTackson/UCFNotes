### Definition 7.1 - Primal Problem
The primal problem is known as the minimization of a specific function that is subject to a specific condition. This can be written out as the following:
$$
\begin{align}
\min_x \;&\;f(x)\\
\text{subject to} \;&\; g_i (x) \leq 0 \;\; \text{for all} \;\; i=1,...,m
\end{align}
$$
In this primal problem above, we are minimizing the function $f(x)$ while corresponding to the **primal variables** $x$.

---
### Remark - Lagrange Multipliers
The Lagrange multipliers are introduce to replace the constraint indicator (step function) with a linear function with the condition of $\lambda_i \geq 0$. By enforcing the condition, the Lagrangian ensures that any violation of an inequality constraint increases the objective value, allowing constrained optimization to be expressed as an unconstrained minimization of the Lagrangian.

### Remark - Lagrangian Function
To combine the objective and the constraints of the Primal Problem, we then form the Lagrangian:
$$
\begin{align}
\mathcal{L}(x,\lambda)=&\;f(x)+\sum^m_{i=1}\lambda_ig_i(x)\\
=&\; f(x)+\lambda^\top g(x)
\end{align}
$$
Where in line 2 we have concatenated all constraints $g_i(x)$ into a vector $g(x)$, and all the Lagrange multipliers.

### Remark - Lagrangian Dual
As spoken about above, the [[#Remark - Lagrange Multipliers|Lagrange Multipliers]] replace the constraint indicators with a linear function. The associated Lagrangian dual problem is given by the following:
$$
\begin{align}
\max_{\lambda\in\mathbb{R}^m} \;&\; \mathcal{D}(\lambda)\\
\text{Subject to} \;&\; \lambda \geq 0,
\end{align}
$$
where $\lambda$ are the dual variables and $D(\lambda)=min_{x\in\mathbb{R}^d} \mathcal{L}(x,\lambda)$. The introduction of the Lagrange multipliers changes the $\min$ of the primal problem to a $\max$ of the Lagrangian Dual because you are now trying to find the **tightest possible lower bound** on the primal objective.

---
### Minimax Inequality & Weak duality
The **minimax inequality** states that for any function with two arguments: 
$$
\begin{matrix}
\gamma(x,y)\text{, the maximin is less then the minimax:}\\
\max_y \min_x \gamma(x,y) \leq \min_x \max_y \gamma (x,y)
\end{matrix}
$$
Furthermore, this inequality introduces the idea of **weak duality** by showing:
$$
\begin{matrix}
\max_{\lambda\geq0} \min_x \mathcal{L}(x,\lambda) \leq \min_x \max_{\lambda\geq0} \mathcal{L}(x,\lambda)
\end{matrix}
$$
We see that the left-hand side is exactly the [[#Remark - Lagrangian Dual|Lagrangian Dual problem]] while the right hand side is the [[#Definition 7.1 - Primal Problem|Primal Problem]]. This showcases the dual objective is always less than or equal to the primal optimum giving a valid lower bound.

---
### Definition 7.2 - Convex set
A set $\mathcal{C}$ is a *convex set* if for any $x,y\in \mathcal{C}$ and for any scalar $\theta$ with $0\leq\theta\leq1$, we have
$$
\theta x + (1-\theta)y\in \mathcal{C}
$$
---
### Definition 7.3 - Convex Function
Let function $f:\mathbb{R}^D \to \mathbb{R}$ be a function whose domain is a convex set. The function $f$ is a *convex function* if for all $x,y$ in the domain of $f$, and for any scalar $\theta$ with $0\leq\theta\leq1$, we have
$$
f(\theta x+ (1-\theta)y)\leq \theta f(x)+(1-\theta)f(y)
$$
**Remark:** A *concave function* is the negative of a convex function

---

