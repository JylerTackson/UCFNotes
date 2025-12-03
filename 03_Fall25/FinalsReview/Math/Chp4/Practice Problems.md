### Problem 4.1 - Determinant 
Compute the determinant using the Laplace expansion (using the first row) and the Sarrus rule for:
$$
A=
\begin{bmatrix}
1&3&5\\
2&4&6\\
0&2&4
\end{bmatrix}
$$

---
### Problem 4.2 - Determinant
Compute the following determinant efficiently:
$$
\begin{bmatrix}
2&0&1&2&0\\
2&-1&0&1&1\\
0&1&2&1&2\\
-2&0&2&-1&2\\
2&0&0&1&1
\end{bmatrix}
$$

---
### Problem 4.3 - Eigen Space
Compute the eigen spaces of:
- $A:=\begin{bmatrix}1&0\\1&1\end{bmatrix}$
- $B:=\begin{bmatrix}-2&2\\2&1\end{bmatrix}$
To compute the eigen space:
1) Find the eigen values:
	1) Setup the Eigen value matrix $A-\lambda I$
2) Calculate Determinant:
	1) $det(A-\lambda I)$
3) Solve the characteristic equation created by the determinant.

#### Part A
Determinant of a $2\times 2$
$$
det(A)=\begin{bmatrix}
a_{11} & a_{12}\\
a_{21} & a_{22}
\end{bmatrix}
=a_{11}a_{22} - a_{21}a_{12}
$$
Therefore we can solve for the characteristic equations doing the following:
$$
\begin{align}
det(A-\lambda I) =&\; 
\begin{bmatrix}
1-\lambda & 0 \\
1 & 1-\lambda
\end{bmatrix}\\\\
=&\;(1-\lambda)(1-\lambda) - (1)\\
=&\; \lambda^2-\lambda\\
=&\; \lambda(\lambda-1)\\\\
\lambda \Rightarrow&\; 
\begin{cases}
\lambda = 1\\
\lambda = 0
\end{cases}
\end{align}
$$
Now that we have the eigen values we can move on to the eigen spaces by plugging in the values to the matrix $A-\lambda I$
$$
\begin{array}{c \qquad c}
\lambda = 1 & \lambda = 0 \\[1em]
A - 1I =
\begin{bmatrix}
1-1 & 0 \\
1   & 1-1
\end{bmatrix}
=
\begin{bmatrix}
0 & 0 \\
1 & 0
\end{bmatrix}
&
A - 0I =
\begin{bmatrix}
1-0 & 0 \\
1   & 1-0
\end{bmatrix}
=
\begin{bmatrix}
1 & 0 \\
1 & 1
\end{bmatrix}
\\
A-1I=
\begin{bmatrix}
0 & 0 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
&
A-0I=
\begin{bmatrix}
1 & 0 \\
1 & 1
\end{bmatrix}
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}
\\
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}=
t\begin{bmatrix}
0\\1
\end{bmatrix}
\therefore\lambda=1\text{ is an eigen value}
&
\begin{bmatrix}
x_1\\x_2
\end{bmatrix}=
\begin{bmatrix}
0\\0
\end{bmatrix}
\therefore\lambda=0\text{ is NOT an eigen value}
\end{array}
$$
We are now able to construct the eigen space for $A$ using the span of the eigen vectors found:
$$
E_\lambda(A)=span[
\begin{bmatrix}
0\\1
\end{bmatrix}
]
$$

#### Part B:


---
### Problem 4.4 - Eigen Space
Compute all eigen spaces of the following:
$$
A=\begin{bmatrix}
0&-1&1&1\\
-1&1&-2&3\\
2&-1&0&0\\
1&-1&1&0
\end{bmatrix}
$$

---

### Problem 4.5 - Diagonalization
Diagonalizability of a matrix is unrelated to its invertibility. Determine for the following four matrices whether they are diagonalizable and/or invertible 
$$
\begin{matrix}
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix},
&&
\begin{bmatrix}
1&0\\
0&0
\end{bmatrix},
&&
\begin{bmatrix}
1&1\\
0&1
\end{bmatrix},
&&
\begin{bmatrix}
0&1\\
0&0
\end{bmatrix}
\end{matrix}
$$
To determine if a matrix is invertible you can use the determinant. If a matrices determinant is $=0$ then the matrix is not invertible. 
$$
\begin{matrix}

\end{matrix}
$$


---
### Problem 4.6 - Eigen Space & Diagonalization
Compute the eigenspaces of the following transformation matrices. Are they diagonalizable?
$$
\begin{matrix}
A=\begin{bmatrix}
2&3&0\\
1&4&3\\
0&0&1
\end{bmatrix}\\\\
B=\begin{bmatrix}
1&1&0&0\\
0&0&0&0\\
0&0&0&0\\
0&0&0&0
\end{bmatrix}\\
\end{matrix}
$$

---
### Problem 4.7 - Diagonalization
Are the following matrices diagonalizable? If yes, determine their diagonal form and a basis with respect to which the transformation matrices are diagonal. If no, give reasons why they are not diagonalizable.

$$
\begin{matrix}
A=\begin{bmatrix}
0&1\\
-8&4
\end{bmatrix}\\\\
B=\begin{bmatrix}
1&1&1\\
1&1&1\\
1&1&1
\end{bmatrix}\\\\
C=\begin{bmatrix}
5&4&2&1\\
0&1&-1&-1\\
-1&-1&3&0\\
1&1&-1&2
\end{bmatrix}\\\\
D=\begin{bmatrix}
5&-6&-6\\
-1&4&2\\
3&-6&-4
\end{bmatrix}\\\\
\end{matrix}
$$

---
### Problem 4.8 - SVD
Find the SVD of the matrix 
$$
A=\begin{bmatrix}
3&2&2\\
2&3&-2
\end{bmatrix}
$$
1) Compute $A^\top A$
$$
A^\top A = 
\begin{bmatrix}
3 & 2 \\
2 & 3 \\
2 & -2
\end{bmatrix}
\begin{bmatrix}
3&2&2\\
2&3&-2
\end{bmatrix}
=
\begin{bmatrix}
13&12&2\\
12&13&-2\\
2&-2&8
\end{bmatrix}
$$
2) Find Eigen Values
$$
det(A-\lambda I)
=
\begin{bmatrix}
13-\lambda&12&2\\
12&13-\lambda&-2\\
2&-2&8-\lambda
\end{bmatrix}

$$

3) 

---
### Problem 4.9 - SVD
Find the SVD of the matrix
$$
A=\begin{bmatrix}
2&2\\
-1&1
\end{bmatrix}
$$
---
### Problem 4.10 - Rank 1 Approximation
Find the rank-1 approximation of the following matrix
$$
A=\begin{bmatrix}
3&2&2\\
2&3&-2
\end{bmatrix}
$$
---
### Problem 4.11
Show that for any $A\in \mathbb{R}^{m\times n}$ the matrices $A^\top A$ and $AA^\top$ possess the same nonzero eigenvalues.

---
### Problem 4.12
Show that for $x\neq0$ Theorem 4.24 holds, i.e., show that
$$
\max_x \frac{||Ax||_2}{||x||_2} = \sigma_1
$$
where $\sigma_1$ is the largest singular value of $A\in\mathbb{R}^{m\times n}$
