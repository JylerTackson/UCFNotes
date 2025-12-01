### Problem 3.1
Show that $\langle\cdot,\cdot\rangle$ defined for all $x=[x_1,x_2]^\top\in\mathbb{R}^2$ and $y=[y_1,y_2]^\top\in\mathbb{R}^2$ by:
$$
\langle x,y \rangle := x_1,y_1-(x_1y_2+x_2y_1)+2(x_2y_2)
$$
is an inner product.

---
### Problem 3.2
Consider $\mathbb{R}^2$ with $\langle \cdot,\cdot \rangle$ defined for all $x$ and $y$ in $\mathbb{R}^2$ as
$$
\langle x,y\rangle :=x^\top
\begin{bmatrix}
2&0\\
1&2
\end{bmatrix}
y
$$
Is $\langle \cdot,\cdot \rangle$ an inner product?

---

### Problem 3.3
Compute the **distance** between the following:
$$
\begin{matrix}
x=\begin{bmatrix}
1\\2\\3
\end{bmatrix},
&&
y=\begin{bmatrix}
-1\\-1\\0
\end{bmatrix}
&&
A=\begin{bmatrix}
2&1&0\\
1&3&-1\\
0&-1&2
\end{bmatrix}
\end{matrix}
$$
using
1. $\langle x, y \rangle := x^\top y$
2. $\langle x, y \rangle := x^\top A y$

---
### Problem 3.4
Compute the **angle** between:

$$\begin{matrix}
x=\begin{bmatrix}
1\\2
\end{bmatrix},
&&
y=\begin{bmatrix}
-1\\-1
\end{bmatrix}
&&
A=\begin{bmatrix}
2&1\\
1&3
\end{bmatrix}
\end{matrix}$$using
1. $\langle x, y \rangle := x^\top y$
2. $\langle x, y \rangle := x^\top B y$

---

### Problem 3.5
Consider the Euclidean vector space $\mathbb{R}^5$ with the dot product. A subspace $U \subseteq \mathbb{R}^5$ and $x\in \mathbb{R}^5$ are given by:
$$
U= \text{span}\left[
\begin{bmatrix}
0\\-1\\2\\0\\2
\end{bmatrix},
\begin{bmatrix}
1\\-3\\1\\-1\\2
\end{bmatrix},
\begin{bmatrix}
-3\\4\\1\\2\\1
\end{bmatrix},
\begin{bmatrix}
-1\\-3\\5\\0\\7
\end{bmatrix}
\right],
\;\;
x=
\begin{bmatrix}
-1\\-9\\-1\\4\\1
\end{bmatrix}
$$
1) Determine the orthogonal projection $\pi_U(x)$ of $x$ onto $U$
2) Determine the distance $d(x,U)$

---

### Problem 3.6
Consider $\mathbb{R}^3$ with the inner product
$$
\langle x,y \rangle := x^\top 
\begin{bmatrix}
2&1&0\\
1&2&-1\\
0&-1&2
\end{bmatrix}
$$
Furthermore, we define $e_1, e_2, e_3$ as the standard canonical basis in $\mathbb{R}^3$
1) Determine the orthogonal projection $\pi_U(e_2)$ of $e_2$ onto
$$
U=\text{span}[e_1, e_3]
$$
2) Compute the distance $d(e_2,U)$
3) Draw the scenario: standard basis vectors and $\pi_U(e_2)$

---
### Problem 3.7
Let $V$ be a vector space and $\pi$ an endomorphism of $V$.
1) Prove that $\pi$ is a projections iff $id_V-\pi$ is a projection, where $id_V$ is the identity endomorphism on $V$.
2) Assume now that $\pi$ is a projection. Calculate $Im(id_V-\pi)$ and $\text{ker}(id_V-\pi)$ as a function of $Im(\pi)$ and $\text{ker}(\pi)$.

---
### Problem 3.8
Using the Gram-Schmidt method, turn the basis $B=(b_1, b_2)$ of two-dimensional subspace $U\subseteq\mathbb{R}^3$ into an $\text{ONB} \;C=(c_1,c_2)$ of $U$, where:
$$
\begin{matrix}
b_1:=
\begin{bmatrix}
1\\1\\1
\end{bmatrix},
&&
b_2:=
\begin{bmatrix}
-1\\2\\0
\end{bmatrix}
\end{matrix}
$$

---
### Problem 3.9
Let $n\in \mathbb{N}$ and let $x_1,...,x_n>0$ be $n$ positive real numbers so that $x_1+...+x_n=1$. Use the Cauchy-Schwarz inequality and sow that:
- **a)** $\sum_{i=1}^n x_i^2\geq \frac{1}{n}$
- **b)** $\sum _{i=1}^n \frac{1}{x_i}\geq n^2$

---
### Problem 3.10
Rotate the vectors by ${30}^{\circ}$
$$
\begin{matrix}
x_1:=
\begin{bmatrix}
2\\3
\end{bmatrix},
&&
x_2:=
\begin{bmatrix}
0\\-1
\end{bmatrix}
\end{matrix}
$$