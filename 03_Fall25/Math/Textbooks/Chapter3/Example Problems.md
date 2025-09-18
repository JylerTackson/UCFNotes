$$
\newcommand{\bra}[1]{\langle#1|}
\newcommand{\ket}[1]{|#1\rangle}
$$
Assignment 2:
- 3.2
- 3.3
- 3.4
- 3.5
- 3.6
- 3.8
- 3.9
---
### Problem 3.1
Show that $<\cdot,\cdot>$ defined for all  $x=[x_1,x_2]^T\in\mathbb{R}^2$ and $y=[y_1,y_2]^T\in\mathbb{R}^2$ by:
$$
\tag{Q\;3.1}
<x,y>:=x_1y_1-(x_1y_2+x_2y_1)+2(x_2y_2)
$$
is an inner product

---
### Problem 3.2
Consider $\mathbb{R}^2$ with $<\cdot,\cdot>$ defined for all $x$ and $y$ in $\mathbb{R}^2$ as:
$$
\tag{Q\;3.2}
<x,y>:=x^T
\left[
\begin{matrix}
2&0\\
1&2
\end{matrix}
\right]
y$$
Is $<\cdot,\cdot>$ an inner product?

---
### Problem 3.3
Compute the distance between
$$
\tag{Q\;3.3}
x=
\left[
\begin{matrix}
1\\2\\3
\end{matrix}
\right]
,\;\;
y=
\left[
\begin{matrix}
-1\\-1\\0
\end{matrix}
\right]$$
using:
$$
\begin{matrix}
\begin{align}
(a) <x,y>:&=x^Ty\\
(b) <x,y>:&=x^TAy
\end{align}
&,&
A:=
\left[
\begin{matrix}
2&1&0\\
1&3&-1\\
0&-1&2
\end{matrix}
\right]
\end{matrix}
$$

---
### Problem 3.4
Compute the angle between:
$$
\tag{Q\;3.4}
x=
\left[
\begin{matrix}
1\\2
\end{matrix}
\right]
,\;\;
y=\left[
\begin{matrix}
-1\\-1
\end{matrix}
\right]
$$using:
$$
\begin{matrix}
\begin{align}
(a) <x,y>:&=x^Ty\\
(b) <x,y>:&=x^TBy
\end{align}
&,&
B:=
\left[
\begin{matrix}
2&1\\
1&3\\

\end{matrix}
\right]
\end{matrix}
$$

---
### Problem 3.5
Consider the Euclidean vector space $\mathbb{R}^5$ with the dot product. A subspace $U\subseteq\mathbb{R}^5$ and $x\in\mathbb{R}^5$ are given by:
$$
\tag{Q\;3.5}
U=span[
\left[
\begin{matrix}
0\\-1\\2\\0\\2
\end{matrix}
\right],
\left[
\begin{matrix}
1\\-3\\1\\-1\\2
\end{matrix}
\right],
\left[
\begin{matrix}
-3\\4\\1\\2\\1
\end{matrix}
\right],
\left[
\begin{matrix}
-1\\-3\\5\\0\\7
\end{matrix}
\right]],\;\;\;\;
x=\left[
\begin{matrix}
-1\\-9\\-1\\4\\1
\end{matrix}
\right],$$
- **(a)** Determine the orthogonal projection $\pi_U(x)$ of $x$ onto $U$
- **(b)** Determine the distance $d(x,U)$

---
### Problem 3.6
Consider $\mathbb{R}^3$ with the inner product
$$
\tag{Q\;3.6}
<x,y>:=x^T
\left[
\begin{matrix}
2&1&0\\
1&2&-1\\
0&-1&2
\end{matrix}
\right]$$
Furthermore, we define $e_1,e_2,e_3$ as the standard/canonical basis in $\mathbb{R}^3$.
- **(a)** Determine the orthogonal projection $\pi_U(e_2)$ of $e_2$ onto:
$$
\tag{Q\;3.6.a}
\begin{matrix}
U=span[e_1,e_3]\\
\text{Hint: Orthogonality is defined through thr inner product.}
\end {matrix}
$$
- **(b)** Compute the distance $d(e_2,U)$
- **(c)** Draw the scenario: standard basis vectors and $\pi_U(e_2)$

---
### Problem 3.7
Let $V$ be a vector space and $\pi$ and endomorphism of $V$.
- **(a)** Prove that $\pi$ is a projection if and only if $\text{id}_{V}-\pi$ is a projection, where $\text{id}_V$ is the identity endomorphism on $V$.
- **(b)** Assume now that $\pi$ is a projection. Calculate $Im(id_v-\pi)$ and $ker (id_v-\pi)$ as a function of $Im(\pi)$ and $ker(\pi)$.

---
### Problem 3.8
Using the **Gram Schmidt method**, turn the basis $B=(b_1,b_2)$ of a two-dimensional subspace $U\subseteq\mathbb{R}^3$ into an $ONB\;C=(c_1,c_2)$ of $U$, where:
$$
\tag{Q\;3.8}
b_1:=
\left[
\begin{matrix}
1\\1\\1
\end{matrix}
\right]
,\;\;\;
b_2;=
\left[
\begin{matrix}
-1\\2\\0
\end{matrix}
\right]
$$

---
### Problem 3.9
Let $n\in\mathbb{N}$ and let $x_1,...,x_n > 0$ be $n$ positive real numbers s.t $x_1+...+x_n=1$. Use the **Cauchy-Schwarz inequality** and show that:
- **(a)** $\sum_{i=1}^n x_i^2 \geq \frac{1}{n}$
- **(b)** $\sum_{i=1}^n \frac{1}{x_i} \geq n^2$
Hint: Think about the dot product on $\mathbb{R}^n$. Then choose specific vectors $x,y\in\mathbb{R}^n$ and apply the Cauchy-Schwarz inequality.

---
### Problem 3.10
Rotate the vectors by $30\degree$:
$$
\tag{Q\;3.10}
x_1:=
\left[
\begin{matrix}
2\\3
\end{matrix}
\right]
,\;\;\;
x_2:=
\left[
\begin{matrix}
0\\-1
\end{matrix}
\right]
$$

