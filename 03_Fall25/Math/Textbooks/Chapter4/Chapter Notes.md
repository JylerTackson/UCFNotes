![[Pasted image 20250929211330.png]]

## 4.1 Determinant and Trace


> [!Theorem] **Theorem 4.1** 
> For any square matrix $A\in\mathbb{R}^{n\times n}$ it holds that $A$ is invertible if and if $det(A)\neq0$
> We have explicit (closed-form) expressions for determinants of small matrices int erms of the elements of the matrix.
> For $n=1$:
> $$det(A)=det(a_{11})=a_{11}$$
> For $n=2$:
> $$det(A)=
> \begin{vmatrix}
> a_{11}&a_{12}\\
> a_{21}&a_{22}
> \end{vmatrix}=
> a_{11}a_{22}-a_{12}a_{21}$$
> For $n=3$:
> $$
> det(A)=
> \begin{vmatrix}
> a_{11}&a_{12}&a_{13}\\
> a_{21}&a_{22}&a_{23}\\
> a_{31}&a_{32}&a_{33}
> \end{vmatrix}=
> a_{11}a_{22}a_{33}+a_{21}a_{32}a_{13}+a_{31}a_{12}a_{23}-a_{31}a_{22}a_{13}-a_{11}a_{32}a_{23}-a_{21}a_{12}a_{33}
> $$

> [!Theorem] **Theorem 4.2 -** Laplace Expansion
> Consider a matrix $A\in\mathbb{R}^{n\times n}$. Then, for all $j=1,...,n:$
> 1) Expansion along column $j$:
> $$det(A)=\sum^n_{k=1}(-1)^{k+j}a_{kj}det(A_{kj})$$
> 2) Expansion along row $j$:
> $$det(A)=\sum^n_{k=1}(-1)^{k+j}a_{jk}det(A_{jk})$$
> Here $A_{kj}\in\mathbb{R}^{(n-1)\times(n-1)}$ is the submatrix of $A$ that we obtain when deleting row $k$ and column $j$.

**For $A\in\mathbb{R}^{n\times n}$ the determinant exhibits the following properties:**
- The determinant of a matrix product is the product of the corresponding determinants, $det(AB)=det(A)det(B)$
- Determinants are invariant to transposition, i.e., $det(A)=det(A^T)$
- If A is regular (invertible), then $det(A^{-1})=\frac{1}{det(A)}$
- Similar matrices possess the same determinant. Therefore, for a linear mapping $\Phi:V\to V$ all transformation matrices $A_{\Phi}$ of $\Phi$ have the same determinant. Thus, the determinant is invariant to the choice of basis of a linear mapping.
- Adding a multiple of a column/row to another one does not change $det(A)$.
- Multiplication of a column/row with $\lambda\in\mathbb{R}$ scales $det(A)$ by $\lambda$. In particular, $det(\lambda A)=\lambda^ndet(A)$
- Swapping two rows/columns changes the sign of $det(A)$.
Due to the last three properties, we can use Gaussian elimination to compute $det(A)$ by bringing $A$ into row-echelon form. We can stop Gaussian elimination when we have $A$ in a triangular form where the elements below or above the diagonal are all 0.

> [!Theorem] **Theorem 4.3 -** Square Matrix Determinant
> A square matrix $A\in\mathbb{R}^{n\times n}$ has $det(A)\neq0$ iff $rk(A)=n$.
> In other words, $A$ is invertible iff it is full rank.


> [!Definition] **Definition 4.4 -** Trace
> The *trace* of a square matrix $A \in \mathbb{R}^{n\times n}$ is defined as:
> $$tr(A):=\sum^n_{i=1}a_{ii}$$
> i.e. , the trace is the sum of the diagonal elements of $A$.
> The trace satisfies the following properties:
> - $tr(A+B)=tr(A)+tr(B)$ for $A,B\in\mathbb{R}^{n\times n}$
> - $tr(\alpha A)=\alpha tr(A), \alpha\in\mathbb{R}$ for $A \in\mathbb{R}^{n\times n}$
> - $tr(I_n)=n$
> - $tr(AB)=tr(BA)$ for $A\in R^{n\times k},B\in\mathbb{R}^{k\times n}$


> [!Definition] **Definition 4.5 -** Characteristic Polynomial
> For $\lambda \in \mathbb{R}$ and a square matrix $A\in\mathbb{R}^{n\times n}$
> $$
> \begin{align}
> p_A(\lambda):=&\;det(A-\lambda I)\\
> =&\;c_0+c_1\lambda+c_2\lambda^2+...+c_{n-1}\lambda^{n-1}+(-1)^n\lambda^n,
> \end{align}
> $$
>$c_0,...,c_{n-1}\in\mathbb{R}$, is the characteristic polynomial of $A$. In particular:
>$$
> \begin{align}
> c_0=&\;det(A)\\
> c_{n-1}=&\;(-1)^{n-1}tr(A)
> \end{align}
>$$
>The characteristic polynomial $p_A(\lambda)$ will allow us to compute **eigen values and eigen vectors**.


---

## 4.2 Eigenvalues and Eigenvectors


> [!Definition] **Definition 4.6 -** Eigenvalue Equation
> Let $A\in\mathbb{R}^{n\times n}$ be a square matrix. Then $\lambda\in\mathbb{R}$ is an eigenvalue of $A$ and $x\in\mathbb{R}^n\text{ and }0\not\in{x}$ is the corresponding eigenvector of $A$ if:
> $$
> Ax=\lambda x
> $$


> [!Definition] **Definition 4.7 -** Collinearity and Codirection
> Two vectors that point in the same direction are called *codirected*. Two vectors that point in the same direction are called **codirected**. Two vectors are **collinear** if they point in the same or the opposite direction.


> [!Theorem] **Theorem 4.8**
> $\lambda\in\mathbb{R}$ is an eigenvalue of $A\in\mathbb{R}^{n\times n}$ iff $\lambda$ is a root of the characteristic polynomial $p_A(\lambda)$ of $A$.


> [!Definition] **Definition 4.9**
> Let a square matrix $A$ have an eigenvalue $\lambda_i$. The algebraic multiplicity of $\lambda_i$ is the number of times the root appears in the **characteristic polynomial.**


> [!Definition] **Definition 4.10 -** Eigen space and spectrum
> For $A\in\mathbb{R}^{n\times n}$, the set of all eigenvectors of $A$ associated with an eigen value $\lambda$ spans a subspace of $\mathbb{R}^n$, which is called the **eigen space** of $A$ with respect to $\lambda$ and is denoted by $E_\lambda$. The set of all eigenvalues of $A$ is called the **eigen spectrum**, or just **spectrum**, of $A$.


> [!Definition] **Definition 4.11**
> Let $\lambda_i$ be an eigenvalue of a square matrix $A$. Then the **geometric multiplicity** of $\lambda_i$ is the number of linearly independent eigen-vectors associated with $\lambda_i$. In other words, it is the dimensionality of the eigenspace spanned by the eigenvectors associated with $\lambda_i$.




