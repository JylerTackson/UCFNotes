Analytic Geometry is the practice of adding geometric interpretation and intuition to all of the concepts taught within [[UCFNotes/03_Fall25/Math/Textbooks/Chapter2/Chapter Notes|chapter 2.]]
![[Pasted image 20250916191355.png]]

---
## 3.1 Norms
**Definition:** A *norm* on a [[UCFNotes/03_Fall25/Math/Textbooks/Chapter2/Chapter Notes#2.4.2 Vector Spaces|vector space]] $V$ is a function s.t:
$$
\tag{norm}
\begin{align}
||\cdot||:\; &V\to \mathbb{R},\\
&x\rightarrowtail||x||,
\end{align}
$$
which assigns each vector $x$ its *length* $||x||\in\mathbb{R}$, s.t for all $\lambda\in\mathbb{R}$ and $x,y\in V$ the following hold:
$$
\begin{align}
1)&\text{ Absolutely homogeneous: }||\lambda x||=|\lambda|\;||x||\\\\
2)&\text{ Triangle Inequality: }||x+y||\leq||x||+||y||\\\\
3)&\text{ Positive definite: }||x||\geq 0 \text{ and }||x||=0\Longleftrightarrow x=0
\end{align}
$$

### Types of Norm's



### Triangle Inequality
In geometric terms, the **triangle inequality** states that **for any triangle**, the **sum of the lengths of any two sides** must be $\geq$ the **length of the remaining side.** The triangle inequality ensures the concept of distance is well-defined, that triangles are constructible, and that geometry, physics, and algorithms based on distance are consistent and reliable.



---
## 3.2 Inner Products
Inner products allow for a way to calculate intuitive geometrical concepts like length, angles, or distances between vectors.
### Dot Product
An example of an inner product is the dot product shown here:
$$
\tag{Dot Product}
x^Ty=\sum^n_{i=1}x_iy_i
$$
The dot product calculates if two vectors are pointing in the same direction by adding all the elements of two vectors that are the same size and providing a scalar value. The value of the scalar shows:
1) **Positive**: Vectors point in the same direction
2) **Negative**: Vectors do NOT point in the same direction
3) **Zero**: Perpendicular Vectors

### General Inner Products


> [!Definition] **Definition 3.2**
> Let $V$ be a vector space and $\Omega:V\times V\to\mathbb{R}$ be a bilinear mapping that takes two vectors and maps them onto a real number. Then:
> - **Symmetric:** $\Omega$ is called symmetric if $\Omega(x,y)=\Omega(y,x)$ for all $x,y\in V$, i.e., **the order of the arguments does not matter**
> - **Positive Definite:** $\Omega$ is called *positive definite* if the following holds true:
> $$\forall x \in V \{0\}:\Omega(x,x)>0,\;\;\Omega(0,0)=0$$

> [!Definition] **Definition 3.3**
> Let $V$ be a vector space and $\Omega: V\times V\to\mathbb{R}$ be a bilinear mapping that takes two vectors and maps them onto a real number. Then:
> - A positive definite, symmetric bilinear mapping $\Omega V\times V\to \mathbb{R}$ is called an *inner product* on $V$. We typically write $<x,y>$ instead of $\Omega(x,y)$
> - The pair $(V,<\cdot,\cdot>)$ is called an *inner product space* or (real) *vector space* with *inner product*. If we use the dot product we then call $(V,<\cdot,\cdot>)$ a Euclidean *vector space*.
> - Within this book a **Euclidean vector space** is referred to as by a an **inner product space**.

### Symmetric, Positive Definite Matrices
Symmetric, Positive Definite Matrices play a key part in machine learning, more specifically in the definition of kernels. 

> [!Definition] Definition 3.4
> A symmetric matrix $\mathbf{A}\in\mathbb{R}^{n\times n}$ that satisfies the following equation:
> $$\forall x \in V {0}:x^T Ax>0$$
> is called *symmetric, *and* positive definite*, or just *positive definite*. If only $\geq$ holds in the above equation, then matrix $\mathbf{A}$ is called *symmetric,* and *positive semidefinite*. 
> 
> Finally, if $\mathbf{A}$ is *symmetric, *and* positive definite*, then:
> $$<x,y>=\hat{x}^TA\hat{y}$$
> defines an inner product with respect to an ordered basis $B$, where $\hat{x}$ and $\hat{y}$ are the coordinate representations of $x,y\in V$ with respect to $B$


> [!Theorem] **Thm 3.5**
> For a real valued, finite-dimensional vector space $V$ and an ordered basis $V$ of $V$, it holds that $<\cdot,\cdot>:V\times V\to\mathbb{R}$ is an **inner product** iff $\exists$ a symmetric, positive definite matrix $\mathbf{A}\in\mathbb{R}^{n\times n}$ with:
> $$<x,y>=\hat{x}^TA\hat{y}$$
> The following properties hold if $\mathbf{A}\in\mathbb{R}^{n\times n}$ is symmetric and positive definite:
> - The null space (kernel) of $\mathbf{A}$ consists only of 0 because $x^TAx>0$ for all $x\neq0$. This implies that $\mathbf{A}x\neq0$ if $x\neq0$
> - The diagonal elements $a_ii$ of $\mathbf{A}$ are positive because $a_{ii}=e_i^TAe_i>0$, where $e_i$ is the *i*'th vector of the standard basis in $\mathbb{R}^n$


---
## 3.3 Lengths and Distances
In [[#3.1 Norms|section 3.1]], we discuss norms that we can use to compute the length of a vector. 

**Remark:** (Cauchy-Schwarz Inequality)
For an inner product vector space $(V,<\cdot,\cdot>)$ the induced norm $||\cdot||$ satisfies the *Cauchy-Schwarz* inequality:
$$|<x,y>|\leq||x||\;||y||$$

> [!Definition] **Def 3.6** - Distance and Metric
> ##### **Distance:**
> Consider and inner product space $(V,<\cdot,\cdot>)$ .
> $$d(x,y):=||x-y||=\sqrt{<x-y,x-y>}$$ 
> The function $d(x,y)$ provides you with the *distance* between $x$ and $y$ for $x,y\in V$.
> 
> **NOTE:** If we use the dot product as the inner product then the distance is called the *Euclidean distance*
> 
> ---
> ##### **Metric:**
> This is just a term used to describe your $d(x,y)$ function, for example, the above metric is Euclidean due to the fact we are using Euclidean distance.
> $$\begin{align}d:\;\;&V\times V\to\mathbb{R}\\&(x,y)\rightarrowtail d(x,y)\end{align}$$
> A metric $d$ satisfies the following:
> 1) $d$ is *positive definite*
> 2) $d$ is symmetric
> 3) *Triangle Inequality*





---
## 3.4 Angles and Orthogonality


> [!Definition] **Def 3.7** - Orthogonality
> Two vectors $x$ and $y$ are *orthogonal* iff $<x,y>=0$, and we write $x\perp y$. If additionally $||x||=1=||y||,$ the vector are **unit vectors^[Vector with magnitude/distance of 1]**, then $x$ and $y$ are *orthonormal*.


> [!Definition] **Def 3.8** - Orthogonal Matrix
> A square matrix $\mathbf{A}\in\mathbb{R}^{n\times n}$ is an *orthogonal matrix* iff its cols are **orthonormal** s.t:
> $$AA^T=I=A^TA,$$
> which implies that
> $$A^-1=A^T$$
> i.e., the inverse is obtained by simply transposing the matrix.



---
## 3.5 Orthonormal Basis
Within section [[UCFNotes/03_Fall25/Math/Textbooks/Chapter2/Chapter Notes#Chapter 2.6 Basis and Rank|2.6 of Chapter 2]], the book characterizes properties of basis vectors and found that in an *n*-dimensional vector space, we need *n* basis vectors, i.e., *n* vectors that are linearly independent. In sections [[#3.3 Lengths and Distances]] and [[#3.4 Angles and Orthogonality]], we used [[#3.2 Inner Products]] to compute the **length of vectors** and the **angle between vectors**. Within this section, a special case is discussed where the **basis vectors are orthogonal to each other** and they are **unit vectors.** This is known as an *Orthonormal Basis:* 
> [!Definition] **Def 3.9** - Orthonormal Basis
> Consider an *n*-dimensional vector space $A$ and a basis $\{b_1,...,b_n\}$ of $V$. If
> $$\begin{align}<b_1,b_j>=0&\;\;\;\;\;\text{for }i\neq j&\;\;\;\;\;(3.33)\\<b_i,b_i>=1&&\;\;\;\;\;(3.34)\end{align}$$
> for all $i,j=1,...,n$ then the basis is called an *orthonormal basis* ($ONB$). If only equation $(3.33)$ is satisfied, then the basis is called an **orthogonal basis**
>
>**NOTE:** $(3.34)$ implies that every basis vector has $\text{length/norm}=1$

---
## 3.6 Orthogonal Complement
Orthogonal Complement comes in play in Chapter 10 when we discuss **linear dimensionality reduction**. However providing a definition for *Orthogonal Complement:*

**Orthogonal Complement:**
- Consider a $D$-dimensional vector space $V$ and an $M$-dimensional sub-space $U\subseteq V$. Then its *orthogonal complement* $U^\perp$ is a $(D-M)$-dimensional subspace of $V$ and contains all vectors in $V$ and contains all vectors in $V$ that are orthogonal to every vector in $U$. Finally, $U\cap U^\perp=\{0\}$ so that any vector $x\in V$ can be uniquely decomposed into:
$$
x=\sum^M_{m=1}\lambda_m b_m +\sum^{D-M}_{j=1}\psi_jb_j^\perp, \;\;\;\; \lambda_m,\psi_j\in\mathbb{R}
$$

---
## 3.7 Inner Product of Functions
An inner product of two functions $u:\mathbb{R}\to\mathbb{R}$ and $v:\mathbb{R}\to\mathbb{R}$ can be defined as the definite integral:
$$
<u,v>:=\int^b_au(x)v(x)dx
$$
for lower and upper limits $a,b<\infty$ respectively.
- If the integral evaluate to $0$ then $u$ and $v$ are orthogonal.

---
## 3.8 Orthogonal Projections


> [!Definition] **Def 3.10** - Projection
> Let $V$ be a vector space and $U \subseteq V$ a subspace of $V$. A linear mapping $\pi:V\to U$ is called a *projection* if:
> $$\pi^2=\pi\circ\pi=\pi$$
>---
> **Projection Matrix:**
> Since we were able to show within [[UCFNotes/03_Fall25/Math/Textbooks/Chapter2/Chapter Notes#Chapter 2.7 Linear Mappings|chapter 2.7 linear mappings]], that a **linear mapping can be expressed by a transformation matrix** we are able to define the *Projection Matrix*. These matrices $P_\pi$, exhibit the property that $P^2_\pi=P_\pi$
###  Projection onto One-Dimensional Subspaces (Lines)



### Projection onto General Subspaces



### Gram-Schmidt Orthogonalization



### Projection onto Affine Subspaces



---
## 3.9 Rotations

### Rotations in $\mathbb{R}^2$


> [!Definition] **Def 3.11** - Givens Rotation
> Let $V$ be an *n*-dimensional Euclidean vector space and $\Phi:V\to V$ an automorphism with transformation matrix:
> $$R_{ij}(\theta):=\left[
> \begin{matrix}
> I_{i-1} & 0 & ... & ... & 0 \\
> 0&cos(\theta) & 0 & -sin(\theta) &0 \\
> 0& 0 & I_{j-i-1} & 0 & 0 \\
> 0& sin(\theta) & 0 & cos(\theta) & 0 \\
> 0& ... & ... & 0 & I_{n-j}
> \end{matrix}
> \right]$$
> for $1\leq i < j \leq n$ and $(\theta) \in \mathbb{R}$. Then $R_{ij}(\theta)$ is called * Givens rotation.* Essentially, $R_{ij}(\theta)$ is the identity matrix $I_n$ with:
> $$r_{ii}=cos(\theta),\;\;\; r_{ij}=-sin(\theta),\;\;\; r_{ji}=sin(\theta),\;\;\; i_{jj}=cos(\theta)$$
> In two dimensions $(i.e., n=2)$, we obtain $(3.76)$ as a special case.


### Rotations in $\mathbb{R}^3$

### Rotations in $\mathbb{R}^n$

---