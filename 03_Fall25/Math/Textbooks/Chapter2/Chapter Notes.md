

# Chapter 2
One major idea is the idea of **"closure"**
- What is the set of all things that can result from my proposed operations?

## Chapter 2.1 Systems of Linear Equations
A system of linear equations:
$$\begin{matrix}
2x_1+3x_2+5x_3=1 \\
4x_1-3x_2-7x_3=8 \\
9x_1+5x_2-3x_3=2
\end{matrix}$$
can be represented through a matrix as follows:
$$\left[
\begin{matrix}
2 & 3 & 5 \\
4 & -2 & -7 \\
9 & 5 & -3 
\end{matrix}\right]

\left[\begin{matrix}x_1\\x_2\\x_3\end{matrix}\right]
=
\left[\begin{matrix}1\\8\\2\end{matrix}\right]
$$
Solving can be found in [[UCFNotes/03_Fall25/Math/Textbooks/Chapter2/Chapter Notes#Chapter 2.3 Solving Systems of Linear Equations|section 2.3]]


## Chapter 2.2 Matrices


#### Definition - Matrix
$\mathbf{A}$ is am $m\cdot n$-tuple of elements $a_{ij}$ which is ordered according to a rectangular scheme consisting of $m$ rows and $n$ cols:

$$A=\left[\begin{matrix}
a_{11} & a_{12} & ... & a_{1n} \\ 
a_{21} & a_{22} & ... & a_{2n} \\ 
\vdots & \vdots &  & \vdots\\ 
a_{m1} & a_{m2} & ... & a_{mn} \\ 
\end{matrix}\right] \text{ Where } a_{ij}\in R$$

#### Matrix Operations
Here is defined the basic operations for Matrices

##### Addition and Subtraction
Assuming you have two matrices
1) $A_{m\times n}$
2) $B_{x\times y}$
When attempting to do addition or subtraction, $A, B$ row and col's must be equal:

$$A\pm B=
\left[
\begin{matrix} 1&2 \\ 0&1 \end{matrix}
\right]
\pm
\left[
\begin{matrix} 3&4 \\ 5&1 \end{matrix}
\right]
=
\left[
\begin{matrix} (1\pm3)&(2\pm4) \\ (0\pm5)&(1\pm1) \end{matrix}
\right]
=
C
$$


##### Multiplication
Assuming you have two matrices
1) $A_{m\times n}$
2) $B_{x\times y}$

When attempting to do multiplication, the adjacent col must = row.
- **If** you are doing $A_{m\times n}\times B_{x \times y}$
	- **Then**: $n=x$
- **else**, if you are doing $B_{x \times y} \times A_{m\times n}$
	- **Then**: $y=m$

Assume $A=\left[\begin{matrix} 1&2 \\ 0&1 \end{matrix}\right]$ and $B=\left[\begin{matrix} 1&1 \\ 1&0 \\ 0&1 \end{matrix}\right]$

The dimensions of $A=[2\times2]$, meanwhile the dimensions of $b=[3\times2]$
Therefor, the only valid multiplication is $B\times A$.

$$B\times A = 
\left[
\begin{matrix}1&1 \\ 1&0 \\ 0&1 \end{matrix}
\right]
\times 
\left[
\begin{matrix} 1&2 \\ 0&1 \end{matrix}
\right]
=
\left[
\begin{matrix}(1+0) & (2+1) \\ (1+0) & (2+0) \\ (0+0) & (0+1) \end{matrix}
\right]
=
\left[
\begin{matrix}1 & 3 \\ 1 & 2 \\ 0 & 1 \end{matrix}
\right]$$

##### Identity Matrix
The $n\times n$ matrix containing 1 on the diagonal and 0 everywhere else:
$$I=\left[\begin{matrix}
1 & 0 & ... & 0 \\ 
0 & 1 & ... & 0 \\ 
\vdots & \vdots & \ddots & \vdots\\ 
0 & 0 & ... & 1 \\ 
\end{matrix}\right]$$
##### Inverse Matrix
Not every matrix $A$ posses an inverse, notated as $A^{-1}$, however if $A$ does posses one then $A$ is considered to be *regular/invertible/nonsingular*. The matrix $A$ has an inverse if it can be reduced using row echelon form and the inverse captured on the side through the echelon transformations.
###### Properties:
$AA^{-1}=I=A^{-1}A$
$(AB)^-1=B^{-1}A^{-1}$
$(A+B)^-1\neq A^{-1}+B^{-1}$

###### Calculating the inverse
To compute the inverse $A^{-1}$ we need to find a matrix $X$ that satisfies $AX=I$. $\therefore$ Then, $X=A^-1$ so we solve $AI=X$ and reduce $A$ to row echelon form.
##### Transpose Matrix
$A^{T}$ can be obtained by writing the columns of $A$ as the rows of $A^{T}$
###### Properties:
1) $(A^T)^T=A$
2) $(AB)^T=B^TA^T$
3) $(A+B)^T=A^T+B^T$


##### Additional Matrix Properties
- Associativity: $(AB)C=A(BC)$
- Distributivity: $(A+B)C=AC+BC$
- Multiplication with the Identity matrix: $\forall A \in R^{m\times n}:(I_mA=AI_n=A)$

---

## Chapter 2.3 Solving Systems of Linear Equations
To solve a system of linear equations using matrix transformations you utilize a small set of elementary transformations to help you solve the system.

1) **Row Swap:** You can swap the location of rows
	- $\text{Example: }R_2 \leftrightarrow R_1$
2) **Row Multiply:** You can multiply a row with a constant.
	- $\text{Example: }R_2\to 4R_2$
3) **Row Replacement:**  Add a multiple of one row to another row.
	- $\text{Example: } R_2\rightarrow R_2-5R_1$

The goal of applying the matrix transformations to your augmented matrix is to reduce it to **row-echelon form:**
$$\begin{matrix}
\begin{matrix}
x_1+x_2+x_3+x_4=0 \\
\;\;\;\;\;\;\;x_2+x_3+x_4=2 \\
\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;x_3 + x_4 = 1 \\
\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;x_4 = -2
\end{matrix}
\\
\downarrow
\\
\left[
\begin{matrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 
\end{matrix}
\right]
\left[
\begin{matrix}
0\\2\\1\\-2
\end{matrix}
\right]

\end{matrix}$$




---
## Chapter 2.4 Vector Spaces

### 2.4.1 Groups
**Definition:**
- Consider a set $\mathcal{G}$ and an operation $\otimes:\mathcal{G}\times \mathcal{G} \to \mathcal{G}$ defined on $\mathcal{G}$. Then $G:=(\mathcal{G},\otimes)$ is called a **group** if the following holds:
	1) **Closure** of $\mathcal{G}$ under $\otimes:\forall x, y\in \mathcal{G}: x\otimes y \in \mathcal{G}$
	2) **Associativity**: $\forall x, y, z\in \mathcal{G}: (x\otimes y)\otimes z = x \otimes (y \otimes z)$
	3) **Neutral** element: $\exists \; e\in \mathcal{g} \;\forall\; x \in \mathcal{G} : x \otimes r = x \text{ and } e\otimes x=x$
	4) **Inverse** element: $\forall\; x \in \mathcal{G} \; \exists \; y \in \mathcal{G} : x\otimes y = e \text{ and } y \otimes x=e, \text{ where } e$ is the neutral element. We often write $x^{-1}$ to denote the inverse element of $x$.

- **Abelian:** If additionally $\forall x, y \in \mathcal{G} : x\otimes y=y\otimes x$ then $G=(\mathcal{G},\otimes)$ is an *Abelian* group **(commutative)**.

**Definition:**
- A General Linear Group, defined as $GL(n,R)$, where the set of regular matrices $A \in R^{n\times n}$ is a group with respect to matrix multiplication.
	- Since Matrix multiplication is NOT commutative, the group is not Abelian.

### 2.4.2 Vector Spaces
Prior to 2.4.2, we looked at sets $\mathcal{G}$ and inner operations on $\mathcal{G},$ i.e., mappings $\mathcal{G}\times\mathcal{G}\to\mathcal{G}$ that only operate on elements in $\mathcal{G}$. In this section we will consider sets that in addition to an inner operation $+$ we will also include an outer operation $\cdot$, the multiplication of a vector $x\in\mathcal{G}$ by a scalar $\lambda \in \mathbb{R}$.
- **Inner** Operation $\approx$ **Addition**
- **Outer** Operation $\approx$ **Scaling**
**Definition:**
- A Vector Space is a real-valued *vector space* $V=(\mathcal{V},+,\cdot)$ is a set $\mathcal{V}$ with two operations:
$$
\begin{matrix}
+:\mathcal{V}\times\mathcal{V}\to\mathcal{V} \\
\cdot:\mathbb{R}\times\mathcal{V}\to\mathcal{V}
\end{matrix}
$$
- where:
	1) $(\mathcal{V},+)$ is an **Abelian** group
	2) **Distributivity**:
		1) $\forall \; \lambda \in \mathbb{R},x,y\in\mathcal{V}:\lambda:\cdot(x+y)=\lambda\cdot x + \lambda  \cdot y$
		2) $\forall\;\lambda,\psi \in \mathbb{R},x\in\mathcal{V}:(\lambda+\psi)\cdot x =\psi\cdot x + \psi \cdot x$
	3) **Associativity** (outer operation): $\forall\; \lambda,\psi \in \mathbb{R},x\in\mathcal{V}:\lambda\cdot(\psi\cdot x)=(\lambda\psi)\cdot x$
	4) **Neutral element** with respect to the outer operation: $\forall x \in \mathcal{V} : 1 \cdot x = x$

### 2.4.3 Vector Subspaces
Vector subspace is a **closed** set contained within the original vector space with the property that when we perform vector space operations on elements within this subspace, we  will never leave it. 

**Definition:**
- Let $V=(\mathcal{V},+,\cdot)$ be a vector space and $\mathcal{U} \subseteq \mathcal{V}, \mathcal{U} \neq \emptyset$. Then $U=(\mathcal{U},+,\cdot)$ is a *vector subspace* of $V$. To determine whether $(\mathcal{U},+,\cdot)$ is a subspace of $V$ we still do need to show:
	1) $\mathcal{U}\neq\emptyset,\text{ in particular: }0\in\mathcal{U}$
	2) Closure of $\mathcal{U}$
		1) With respect to the outer operation: $\forall \lambda \in \mathbb{R} \forall x \in \mathcal{U} : \lambda x \in \mathcal{U}$
		2) With respect to the inner operation: $\forall x, y\in \mathcal{U} : x + y \in \mathcal{U}$

## Chapter 2.5 Linear Independence



## Chapter 2.6 Basis and Rank

### 2.6.1 Generating Set and basis

### 2.6.2 Rank




## Chapter 2.7 Linear Mappings


### 2.7.1 Matrix Representation of Linear mappings

### 2.7.2 Basis Change

### 2.7.3 Image and Kernel




## Chapter 2.8 Affine Spaces

### 2.8.1 Affine Subspaces

### 2.8.2 Affine Mappings




