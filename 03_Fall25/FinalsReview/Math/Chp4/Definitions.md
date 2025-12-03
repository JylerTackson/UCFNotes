

### Definition 4.19 - Diagonalizable
A matrix $A\in\mathbb{R}^{n\times n}$ is diagonalizable if it is similar to a diagonal matrix, i.e., if there exists an inversible matrix $P\in \mathbb{R}^{n\times n}$ such that 
$$D=P^{-1} A P$$
Where:
- $D\to$ is a matrix whose diagonal elements are the eigen values of $A$
- $P\to$ is a matrix whose columns are the eigenvectors of $A$
A matrix $A\in\mathbb{R}^{n×n}$ is diagonalizable **if and only if** the eigenvectors of $A$ span $\mathbb{R}^n$.

---
### Theorem 4.22 - SVD
Let $A\in\mathbb{R}^{m\times n}$ be a rectangular matrix of rank $r\in [0,\min(m,n)]$. The SVD of $A$ is a decomposition of the form:
$$
A^{m\times n} = U \; \Sigma \; V^\top
$$
- $U^{m\times m} \to$ Orthogonal matrix containing left singular vectors
- $\Sigma^{m \times n}\to$ Diagonal matrix containing the singular values
- $V^{n\times n}\to$ Orthogonal matrix containing the right singular vectors  

#### Algorithm
1) Compute $A^\top A$
2) Solve for the eigen values: $\Lambda = [\lambda_1 ,..., \lambda_d]$
3) Solve for the singular values: $\sigma = [\sigma_1 ,..., \sigma_d] = [\sqrt{\lambda_1} ,..., \sqrt{\lambda_d}]$
	- Create Singular value matrix $\Sigma = \begin{bmatrix}\sigma_1&\cdots &0\\\vdots & \ddots & \vdots \\ 0 & \cdots & \sigma_d\end{bmatrix}$
4) Solve for the right singular vectors: $V=[v_1, ..., v_d]$
	- You do this by normalizing the eigen vectors
5) Calculate the left singular matrix:
	- Each left singular vector forms a column $U$: $u_i=\frac{1}{\sigma_i}Av_i$

---
### Remark - Rank 1 Approximation
The rank 1 approximation can be written as the following:
$$
\bar{A}(k) :=\sigma_i u_iv_i^\top
$$
