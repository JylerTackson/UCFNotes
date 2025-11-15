### Linear Programming
For the special case when all the preceding functions are linear: 
$$
\begin{matrix}
\min_{x\in\mathbb{R}^4}c^Tx\\
\text{Subject to }\; Ax\leq b,
\end{matrix}$$
Where $A\in \mathbb{R}^{x\times d}$ and $b\in \mathbb{R}^m$. These problems have:
- $d$ variables
- $m$ linear constraints

#### Lagrangian
The Lagrangian is a trick used in optimization that lets you merge the objective function and the constraints into a single function. The Lagrangian is defined by:
$$\mathcal{L}(x,\lambda)=c^Tx+\lambda^T(Ax-b)$$
where $\lambda\in\mathbb{R}^m$ is the **vector of non-negative Lagrange multipliers**. 

**NOTE**: Depending on the operation you are doing, the sign changes for the Lagrangian as follows:
- $\max\to \lambda^\top(b-Ax)$ 
- $\min\to \lambda^\top(Ax-b)$

##### Lagrange multiplers
The Lagrange multipliers are solved for by taking the derivative of the Lagrangian, w.r.t $x$, and plugging it into the slack equation to solve for the stationarity of your Lagrange multiplier. Each constraint gives a product as follows:
$$
\lambda_i \cdot \text{slack}_i=0
$$
Which either forces $\lambda_i=0$ or forces the constraint to be tight. You are unable to solve for $\lambda_i$ without first solving for their stationarity first. The derivative of $\mathcal{L}(x,\lambda)$ w.r.t $x$ is as follows:
$$
c+A^T\lambda=0
$$


---

## Exercise 7.5 Express the following optimization problem as a standard linear program in matrix notation: $$\max_{x \in \mathbb{R}^2, \xi \in \mathbb{R}} p^T x + \xi$$ subject to the constraints that: $$\xi \ge 0, x_0 \le 0 \text{ and } x_1 \le 3.$$ To begin, we first need to define our Lagrangian so that we can combine our objective and constraints into a single function to start the optimization process. As defined in section $\mathbf{7.3.1}$ of the book, the Lagrangian for a linear program is defined as follows: $$\tag{7.40} \mathcal{L}(x,\lambda)=c^Tx+\lambda^T(Ax-b) $$ where $\lambda\in\mathbb{R}^m$ is the vector of non-negative Lagrange multipliers. Using our constraints to construct our A matrix and b vector we get the following: $$ \begin{matrix} A=\begin{bmatrix} 1&0&0\\ 0&1&0\\ 0&0&-1 \end{bmatrix}, b=\begin{bmatrix} 0\\3\\0 \end{bmatrix} \\\\ Ax-b= \begin{bmatrix} 1&0&0\\ 0&1&0\\ 0&0&-1 \end{bmatrix} \begin{bmatrix} x_0\\x_1\\\xi \end{bmatrix}- \begin{bmatrix} 0\\3\\0 \end{bmatrix}= \begin{bmatrix} x_0\\x_1-3\\-\xi \end{bmatrix} \end{matrix} $$ Furthermore, using the information defined in the problem, we can define our Lagrangian as follows: $$ \begin{align} \mathcal{L}(x,\lambda)=&\;(p^Tx+\xi)+\lambda^T(Ax-b)\\ =&\; (p_0x_0+p_1x_1+1\xi) + \big(\lambda_0x_0+\lambda_1(x_1-3)+\lambda_2(-\xi)\big) \end{align} $$ To solve for the Lagrange multipliers we will use the derivative of $\mathcal{L}(x,\lambda)$, with respect to $x$, and setting it to zero. This definition is provided in the textbook as: $$ \tag{7.42} c+A^T\lambda=0 $$ This then results in: $$ \begin{align} c+A^T\lambda=&\;0\\ \begin{bmatrix} p_0\\p_1\\1 \end{bmatrix}+ \begin{bmatrix} 1&0&0\\ 0&1&0\\ 0&0&-1 \end{bmatrix} \begin{bmatrix} \lambda_0\\\lambda_1\\\lambda_2 \end{bmatrix} =&\;0\\ \begin{bmatrix} p_0\\p_1\\1 \end{bmatrix}+ \begin{bmatrix} \lambda_0\\\lambda_1\\-\lambda_2 \end{bmatrix} =&\;0\\ \begin{bmatrix} p_0+\lambda_0\\p_1+\lambda_1\\1-\lambda_2 \end{bmatrix} =&\;0 \end{align} $$ Therefore we have a system of equations where we can now deduce the stationarity for the Lagrange multipliers as follows: $$ \begin{matrix} \lambda_0=-p_0 && \lambda_1=-p_1 && \lambda_2=1 \end{matrix} $$ Now that we have the stationarity of the slack equations, we can rewrite the primal constrains $x_0,x_1,\xi$ as follows: $$ \begin{align} a^T_ix\leq&\; b_i\\ \lambda(a^T_ix-b_i)=&\;0 \end{align} $$ $$ \begin{align} \begin{matrix} \begin{bmatrix} 1\\0\\0 \end{bmatrix} x_0 \leq 0 && \begin{bmatrix} 0\\1\\0 \end{bmatrix} x_1 \leq 3 && \begin{bmatrix} 0\\0\\-1 \end{bmatrix} \xi \geq 0 \\\\ \lambda_0(x_0-0)=0 && \lambda_1(x_1-3)=0 && \lambda_2(-\xi-0)=0 \end{matrix} \end{align} $$ Now plugging in the stationarity we found earlier we get: $$ \begin{matrix} -p_0(x_0)=0 && -p_1(x_1-3)=0 && 1(-\xi)=0 \\\\ \boxed{p_0=0 \;\text{OR}\; x_0=0} && \boxed{p_1=0 \;\text{OR}\; x_1=3} && \boxed{\xi=0} \end{matrix} $$ However since these values return OR-conditions you do not plug them in and just continue to solve. To continue solving for the Lagrangian we get: $$ \begin{align} \mathcal{L}(x,\lambda)=&\; (p_0x_0+p_1x_1+1\xi) + \big(\lambda_0x_0+\lambda_1(x_1-3)+\lambda_2(-\xi)\big)\\ =&\; \cancel{p_0x_0}+p_1x_1+\cancel{\xi} \cancel{-p_0x_0}-p_1(x_1-3)\cancel{-\xi}\\ =&\; \cancel{p_1x_1}\cancel{-p_1x_1}+p_13\\ &\therefore\\ \mathcal{L}(x,\lambda)=&\; p_13 \end{align} $$
