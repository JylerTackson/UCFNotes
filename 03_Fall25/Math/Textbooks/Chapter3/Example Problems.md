$$
\newcommand{\bra}[1]{\langle#1|}
\newcommand{\ket}[1]{|#1\rangle}
$$
Assignment 2:
- 3.2✔️
- 3.3✔️
- 3.4✔️
- 3.5✔️
- 3.6✔️
- 3.8✔️
- 3.9❌
---
### Problem 3.1
Show that $\langle\cdot\mid\cdot\rangle$ defined for all  $x=[x_1,x_2]^T\in\mathbb{R}^2$ and $y=[y_1,y_2]^T\in\mathbb{R}^2$ by:
$$
\tag{Q\;3.1}
<x,y>:=x_1y_1-(x_1y_2+x_2y_1)+2(x_2y_2)
$$
is an inner product

---
### Problem 3.2
Consider $\mathbb{R}^2$ with $\langle\cdot,\cdot\rangle$ defined for all $x$ and $y$ in $\mathbb{R}^2$ as:
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

To solve this, I am going to utilize **Theorem 3.5:**
> [!Theorem] **Thm 3.5**
> For a real valued, finite-dimensional vector space $V$ and an ordered basis $V$ of $V$, it holds that $\langle\cdot,\cdot\rangle:V\times V\to\mathbb{R}$ is an **inner product** iff $\exists$ a symmetric, positive definite matrix $\mathbf{A}\in\mathbb{R}^{n\times n}$ with:
> $$<x,y>=\hat{x}^TA\hat{y}$$
> The following properties hold if $\mathbf{A}\in\mathbb{R}^{n\times n}$ is symmetric and positive definite:
> - The null space (kernel) of $\mathbf{A}$ consists only of 0 because $x^TAx>0$ for all $x\neq0$. This implies that $\mathbf{A}x\neq0$ if $x\neq0$
> - The diagonal elements $a_ii$ of $\mathbf{A}$ are positive because $a_{ii}=e_i^TAe_i>0$, where $e_i$ is the *i*'th vector of the standard basis in $\mathbb{R}^n$

Where:
- $A=\left[\begin{matrix}2&0\\1&2\end{matrix}\right]$

**First**, I must show that this is a symmetric positive definite matrix. To show that this is a symmetric, positive definite matrix I would utilize **Definition 3.4** however we can see that $A$ is **NOT** symmetric $\therefore\langle\cdot,\cdot\rangle$ is **NOT** an inner product  

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
(a)&& \langle x,y\rangle:&=x^Ty\\
(b)&& \langle x,y\rangle:&=x^TAy
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

- **(a)**
$$
\begin{align}
\langle x,y \rangle_a :=&\;x^Ty := \left[\begin{matrix}1&2&3\end{matrix}\right] \left[\begin{matrix}-1\\-1\\0\end{matrix}\right]\\
:=&(-1\times-1)+(2\times-1)+(3\times0)\\
:=&(-1)+(-2)+(0)\\
\langle x,y \rangle_a :=&-3\\

\end{align}
$$
- **(b)**
$$
\begin{align}
\langle x,y \rangle_b :=&x^TAy=\left[\begin{matrix}1&2&3\end{matrix}\right] \left[
\begin{matrix}
2&1&0\\
1&3&-1\\
0&-1&2
\end{matrix}
\right]\left[\begin{matrix}-1\\-1\\0\end{matrix}\right]\\
:=&\left[\begin{matrix}((1\times2)+(2\times1)+(0))&((1\times1)+(2\times3)+(3\times-1))&((1\times0)+(2\times-1)+(3\times2))\end{matrix}\right]\left[\begin{matrix}-1\\-1\\0\end{matrix}\right]\\
:=&\left[\begin{matrix}4&4&4\end{matrix}\right]\left[\begin{matrix}-1\\-1\\0\end{matrix}\right]\\
:=&(4\times-1)+(4\times-1)+(4\times0)\\
\langle x,y\rangle_b:=&-8
\end{align}
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
To answer this problem, in section 3.4 of the book, it states "inner products also capture the geometry of a vector space by defining the angle $\omega$ between two vectors."
$$\begin{align}
cos\;\omega=\;&\frac{\langle x,y\rangle}{||x|| \; ||y||}\\
\therefore\\
\omega=\;&cos^{-1}\bigg(\frac{\langle x,y\rangle}{||x||\;||y||}\bigg)
\end{align}$$
- **(a)**
$$\begin{align}
\\\\&\text{Solving for \langle x,y\rangle}\\
\langle x,y\rangle_a:=x^Ty:=&\left[\begin{matrix}1&2\end{matrix}\right]\left[\begin{matrix}-1\\-1\end{matrix}\right]\\
:=&(1\times-1)+(2\times-1)\\
\langle x,y\rangle_a:=& -3\\
\\\\&\text{Solving for ||x||}\\
||x|| =\;&\sqrt{\langle x,x\rangle} = \sqrt{\left[\begin{matrix}1&2\end{matrix}\right]\left[\begin{matrix}1\\2\end{matrix}\right]}\\
=&\sqrt{(1+4)}=\\
||x||=&\sqrt{5}= 2.24\\
\\\\&\text{Solving for ||y||}\\
||y|| =\;&\sqrt{\langle y,y\rangle} = 
\sqrt{\left[\begin{matrix}-1&-1\end{matrix}\right]\left[\begin{matrix}-1\\-1\end{matrix}\right]}\\
=&\sqrt{(1+1)}=\\
||y||=&\sqrt{2}= 1.41\\
\\\\
&\therefore \text{We know that}\\
\omega=\;&cos^{-1}\bigg(\frac{\langle x,y\rangle}{||x||\;||y||}\bigg)\\
\omega=\;&cos^{-1}\bigg(\frac{-3}{2.24\;1.41}\bigg)\\\\
\omega=\;&161.78\degree
\end{align}$$
- **(b)**
$$\begin{align}
\\\\&\text{Solving for \langle x,y\rangle}\\
\langle x,y\rangle_b:=x^TBy:=&
\left[\begin{matrix}1&2\end{matrix}\right]
\left[\begin{matrix}2&1\\1&3\\\end{matrix}\right]
\left[\begin{matrix}-1\\-1\end{matrix}\right]\\
:=&
\left[\begin{matrix}((1\times2)+(2\times1))&((1\times1)+(2\times3))\end{matrix}\right]
\left[\begin{matrix}-1\\-1\end{matrix}\right]\\
:=&
\left[\begin{matrix}4&7\end{matrix}\right]
\left[\begin{matrix}-1\\-1\end{matrix}\right]\\
\langle x,y\rangle_b:=& -11\\
\\\\&\text{Solving for ||x||}\\
||x|| =\;&\sqrt{\langle x,x\rangle} = \sqrt{
\left[\begin{matrix}1&2\end{matrix}\right]
\left[\begin{matrix}2&1\\1&3\\\end{matrix}\right]
\left[\begin{matrix}1\\2\end{matrix}\right]}\\
=&\sqrt{
\left[\begin{matrix}4&7\end{matrix}\right]
\left[\begin{matrix}1\\2\end{matrix}\right]}\\
=&\sqrt{(4+14)}=\\
||x||=&\sqrt{18}= 4.24\\
\\\\&\text{Solving for ||y||}\\
||y|| =\;&\sqrt{\langle y,y\rangle} =
\sqrt{
\left[\begin{matrix}-1&-1\end{matrix}\right]
\left[\begin{matrix}2&1\\1&3\\\end{matrix}\right]
\left[\begin{matrix}-1\\-1\end{matrix}\right]}\\
=&\sqrt{
\left[\begin{matrix}-3&-4\end{matrix}\right]
\left[\begin{matrix}-1\\-1\end{matrix}\right]}\\
=&\sqrt{(3+4)}=\\
||y||=&\sqrt{7}= 2.65\\
\\\\
&\therefore \text{We know that}\\
\omega=\;&cos^{-1}\bigg(\frac{\langle x,y\rangle}{||x||\;||y||}\bigg)\\
\omega=\;&cos^{-1}\bigg(\frac{-11}{4.24\;2.65}\bigg)\\\\
\omega=\;&168.24\degree
\end{align}$$



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

To solve for the orthogonal projection $\pi_U(x)$ of $x$ onto $U$ we will utilize formula $3.58$ within Chapter 3.8 of the book.

> [!Formula] **Formula 3.8 -** Orthogonal Projection
> Once we establish that $\pi_U(x) = B\lambda$, to find the projection $\pi_U(x)\in U$ we use the following formula:
> $$
> \pi_U(x)=B(B^TB)^{-1}B^Tx
> $$

To define B, we must first take the span $U$ and perform Row Reduction. $B$ must contain **ONLY** linearly independent vectors.
$$
\begin{align}
U=
&\begin{bmatrix}
0&1&-3&-1\\
-1&-3&4&-3\\
2&1&1&5\\
0&-1&2&0\\
2&2&1&7
\end{bmatrix} \tag{Define U}\\\\
\Downarrow
U_{RREF}=
&\begin{bmatrix}
1&0&0&1\\
0&1&0&2\\
0&0&1&1\\
0&0&0&0\\
0&0&0&0
\end{bmatrix} \tag{Define RREF U}\\\\
\end{align}
$$

$\therefore$ $B$ will contain the first 3 vectors of $U$.

$$
\begin{align}
\pi_U(x)=&B(B^TB)^{-1}B^Tx\\
=&B\Bigg(
\begin{bmatrix}
0  & -1 & 2 & 0 & 2 \\
1  & -3 & 1 & -1 & 2 \\
-3 & 4  & 1 & 2 & 1
\end{bmatrix}
\begin{bmatrix}
0&1&-3\\
-1&-3&4\\
2&1&1\\
0&-1&2\\
2&2&1
\end{bmatrix}
\Bigg)^{-1}
B^Tx\\
=&B\Bigg(
\begin{bmatrix}
9&9&0\\
9&16&-14\\
0&-14&31\\
\end{bmatrix}
\Bigg)^{-1}
B^Tx\\
=&B\Bigg(
\begin{bmatrix}
\frac{100}{63}&\frac{-31}{21}&\frac{-2}{3}\\
-\frac{31}{21}&\frac{31}{21}&\frac{2}{3}\\
-\frac{2}{3}&\frac{2}{3}&\frac{1}{3}\\
\end{bmatrix}
\Bigg)
B^Tx\\
=&B\Bigg(
\begin{bmatrix}
9&9&0\\
9&16&-14\\
0&-14&31\\
\end{bmatrix}
\Bigg)^{-1}
B^Tx\\
=&
\begin{bmatrix}
0&1&-3\\
-1&-3&4\\
2&1&1\\
0&-1&2\\
2&2&1
\end{bmatrix}
\begin{bmatrix}
\frac{100}{63}&\frac{-31}{21}&\frac{-2}{3}\\
-\frac{31}{21}&\frac{31}{21}&\frac{2}{3}\\
-\frac{2}{3}&\frac{2}{3}&\frac{1}{3}\\
\end{bmatrix}
\begin{bmatrix}
0  & -1 & 2 & 0 & 2 \\
1  & -3 & 1 & -1 & 2 \\
-3 & 4  & 1 & 2 & 1
\end{bmatrix}
\begin{bmatrix}
-1\\-9\\-1\\4\\1
\end{bmatrix}\\
\pi_U(x)=&
\begin{bmatrix}
1\\-5\\-1\\-2\\3
\end{bmatrix}\\
\end{align}
$$

- **(b)** Determine the distance $d(x,U)$
To determine the distance between $x\Longleftrightarrow U$ we will use the $||x-\pi_U(x)||$ 
$$
\begin{align}
x-\pi_U(x)=&
\begin{bmatrix}
-1\\-9\\-1\\4\\1
\end{bmatrix}
-
\begin{bmatrix}
1\\-5\\-1\\-2\\3
\end{bmatrix}
=
\begin{bmatrix}
-2\\-4\\0\\6\\-2
\end{bmatrix}
\end{align}
$$
$$\therefore$$
We can now calculate $||x-\pi_U(x)||$
$$
\begin{align}
||x-\pi_U(x)||=&
\sqrt{\langle x-\pi_U(x), x-\pi_U(x)\rangle}\\
=&
\sqrt{
\begin{bmatrix}
-2&-4&0&6&-2
\end{bmatrix}
\begin{bmatrix}
-2\\-4\\0\\6\\-2
\end{bmatrix}
}\\
=&
\sqrt{(2)^2+(4)^2+(0)^2+(6)^2+(2)^2}\\
=&
\sqrt{60}\\
d(x,U)=&
2\sqrt{15}
\end{align}
$$
---
### Problem 3.6
Consider $\mathbb{R}^3$ with the inner product
$$
\tag{Q\;3.6}
<x,y>:=x^T
\begin{bmatrix}
2&1&0\\
1&2&-1\\
0&-1&2
\end{bmatrix}
y
$$
Furthermore, we define $e_1,e_2,e_3$ as the standard/canonical basis in $\mathbb{R}^3$.
- **(a)** Determine the orthogonal projection $\pi_U(e_2)$ of $e_2$ onto:
$$
\tag{Q\;3.6.a}
\begin{matrix}
U=span[e_1,e_3]\\
\text{Hint: Orthogonality is defined through the inner product.}
\end {matrix}
$$
We know that $e_1, e_2,$ and $e_3$ are the standard/canonical basis in $\mathbb{R}^3\therefore$
$$
U=span[e_1,e_2]=span[
\begin{bmatrix}
1\\0\\0\\
\end{bmatrix},
\begin{bmatrix}
0\\0\\1
\end{bmatrix}
]
$$
For an orthogonal projection with a general inner product we can use **Formula 3.8** to find $\pi_{U}(e_2)$:
> [!Formula] **Formula** Orthogonal Projection on standard basis using general inner product
> Once we establish that $\pi_U(x) = B\lambda$, to find the projection $\pi_U(x)\in U$ we use the following formula:
> $$
> \pi_U(x)=B(B^TAB)^-1B^TAx
> $$

Since $U$ is already in $RREF$ we can say that $U=B$ and we are solving for $x=e_2\therefore$
$$
\begin{align}
\pi_U(x)=&\;B(B^TAB)^-1B^TAe_2\\
=&\;B\Biggl(
\begin{bmatrix}
1&0&0\\
0&0&1
\end{bmatrix}
\begin{bmatrix}
2&1&0\\
1&2&-1\\
0&-1&2
\end{bmatrix}
\begin{bmatrix}
1&0\\
0&0\\
0&1
\end{bmatrix}
\Biggl)^{-1}
B^TA
e_2\\
=&\;
\begin{bmatrix}
1&0\\
0&0\\
0&1
\end{bmatrix}
\Biggl(
\begin{bmatrix}
\frac{1}{2}&0\\
0&\frac{1}{2}
\end{bmatrix}
\Biggl)
\begin{bmatrix}
1&0&0\\
0&0&1
\end{bmatrix}
\begin{bmatrix}
2&1&0\\
1&2&-1\\
0&-1&2
\end{bmatrix}
\begin{bmatrix}
0\\
1\\
0
\end{bmatrix}\\
=&\;
\begin{bmatrix}
\frac{1}{2}&0\\
0&0\\
0&\frac{1}{2}
\end{bmatrix}
\begin{bmatrix}
1&0&0\\
0&0&1
\end{bmatrix}
\begin{bmatrix}
2&1&0\\
1&2&-1\\
0&-1&2
\end{bmatrix}
\begin{bmatrix}
0\\
1\\
0
\end{bmatrix}\\
=&\;
\begin{bmatrix}
\frac{1}{2}&0&0\\
0&0&0\\
0&0&\frac{1}{2}
\end{bmatrix}
\begin{bmatrix}
1\\
2\\
-1
\end{bmatrix}\\
\pi_U(x)=&\;
\begin{bmatrix}
\frac{1}{2}\\
0\\
-\frac{1}{2}
\end{bmatrix}
\end{align}
$$

- **(b)** Compute the distance $d(e_2,U)$

To compute the distance $d(e_2,U)$ we will use the following procedure:
$$\begin{align}
d(e_2,U)=&\;e_2-\pi_U(e_2)\\
=&\;
\begin{bmatrix}
0\\1\\0
\end{bmatrix}
-
\begin{bmatrix}
\frac{1}{2}\\
0\\
-\frac{1}{2}
\end{bmatrix}\\
=&\;
\begin{bmatrix}
-\frac{1}{2}\\
1\\
-\frac{1}{2}
\end{bmatrix}
\end{align}$$


- **(c)** Draw the scenario: standard basis vectors and $\pi_U(e_2)$

![[Desmos _ 3D Graphing Calculator-1.png]]

---
### Problem 3.7
Let $V$ be a vector space and $\pi$ and endomorphism of $V$.
- **(a)** Prove that $\pi$ is a projection if and only if $\text{id}_{V}-\pi$ is a projection, where $\text{id}_V$ is the identity endomorphism on $V$.
- **(b)** Assume now that $\pi$ is a projection. Calculate $Im(id_v-\pi)$ and $ker (id_v-\pi)$ as a function of $Im(\pi)$ and $ker(\pi)$.

---
### Problem 3.8
Using the **Gram Schmidt method**, turn the basis $B=(b_1,b_2)$ of a two-dimensional subspace $U\subseteq\mathbb{R}^3$ into an Orthonormal Basis $(ONB)\;C=(c_1,c_2)$ of $U$, where:
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
Restating the definition of **The Gram Schmidt method** from section 3.8 of the book:
> [!Gram Schmidt] Gram - Schmidt Orthogonalization
> The *Gram-Schmidt orthogonalization method* iteratively constructs an orthogonal basis $(u_1,...,u_n)$ from an basis $(b_1,...,b_n)$ of V as follows:
> $$
> \begin{align}
> u_1:=\;&b_1&(3.67)\\
> u_k:=\;&b_k-\pi_{span[u_1,...,u_{k-1}]}(b_k),\;\;\;k=2,...,n&(3.68)
> \end{align}
> $$
> 
> In **3.68**, the *k*th basis vector $(\mathbf{b_k})$ is projected onto the subspace spanned by the first $k-1$ orthogonal vectors that create the orthogonal basis.

To begin:
$$
\begin{align}
c_1=\;&
b_1=
\begin{bmatrix}
1\\1\\1
\end{bmatrix}\\\\
c_2=\;&
b_2-\pi_{span_{[c_1]}}(b_2)
=
b_2-\frac{c_1c_1^T}{||c_1||^2}b_2\\
=\;&
\begin{bmatrix}
-1\\2\\0
\end{bmatrix}
-
\frac{
\begin{bmatrix}
1\\1\\1
\end{bmatrix}
\begin{bmatrix}
1&1&1
\end{bmatrix}
}{
(1^2+1^2+1^2)
}
\begin{bmatrix}
-1\\2\\0
\end{bmatrix}
\\
=\;&
\begin{bmatrix}
-1\\2\\0
\end{bmatrix}
-
\frac{1}{3}
\begin{bmatrix}
1&1&1\\
1&1&1\\
1&1&1
\end{bmatrix}
\begin{bmatrix}
-1\\2\\0
\end{bmatrix}
\\
=\;&
\begin{bmatrix}
-1\\2\\0
\end{bmatrix}
-
\frac{1}{3}
\begin{bmatrix}
1\\1\\1
\end{bmatrix}\\
c_2=\;&
\begin{bmatrix}
-4/3\\5/3\\-1/3
\end{bmatrix}
\\
\end{align}
$$
Now we have an **Orthogonal Basis** $C=\{c_1,c_2\}$ that we created using the **Gram Schmidt Method**. To create an **Orthonormal Basis** we need to normalize the vectors within the Basis:
$$
\begin{matrix}
\hat{c_1}=\frac{c_1}{|c_1|}&&&&&\hat{c_2}=\frac{c_2}{|c_2|}\\\\
=\frac{1}{\sqrt{3}}
\begin{bmatrix}
1\\1\\1\\
\end{bmatrix}
&&&&&
=\sqrt{\frac{9}{38}}
\begin{bmatrix}
-4/3\\5/3\\-1/3\\
\end{bmatrix}
\end{matrix}
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

