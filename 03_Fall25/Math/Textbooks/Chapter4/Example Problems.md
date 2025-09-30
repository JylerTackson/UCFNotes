Assignment 3:
- 4.2✔️
- 4.4❌
- 4.6❌
- 4.7a-b❌
- 4.8❌
- 4.10❌
- 4.12❌
---
### Problem 4.2
Compute the following determinant efficiently:
$$
\begin{align}\tag{Q\;4.2}
A=
\begin{bmatrix}
2&0&1&2&0\\
2&-1&0&1&1\\
0&1&2&1&2\\
-2&0&2&-1&2\\
2&0&0&1&1
\end{bmatrix}
\end{align}
$$

An $n\times n$ matrix exhibits the following properties:
- Adding a multiple of a column/row to another one does not change $det(A)$.
- Multiplication of a column/row with $\lambda \in \mathbb{R}$ scales $det(A)$ by $\lambda$. In Particular, $det(\lambda A)=\lambda^n det(A)$
- Swapping two rows/columns changes the sign of $det(A)$.
Due to the last three properties, we can use Gaussian elimination to compute $det(A)$ by bringing $A$ into row-echelon form. We can stop Gaussian elimination when we have $A$ in a triangular form where the elements below or above the diagonal are all 0.

$$
\begin{align}\tag{A\;4.2}
A=&\;
\begin{bmatrix}
2&0&1&2&0\\
2&-1&0&1&1\\
0&1&2&1&2\\
-2&0&2&-1&2\\
2&0&0&1&1
\end{bmatrix}\\\\
=&\;
\begin{bmatrix}
2&0&1&2&0\\
0&-1&-1&-1&1\\
0&1&2&1&2\\
0&0&3&1&2\\
0&0&-1&-1&1
\end{bmatrix}\\
&Row_2 = (-1)Row_1+Row_2\\
&Row_4 = (1)Row_1+Row_4\\
&Row_5 = (-1)Row_1+Row_5\\\\
=&\;
\begin{bmatrix}
2&0&1&2&0\\
0&-1&-1&-1&1\\
0&0&-1&-1&1\\
0&0&0&-2&5\\
0&0&1&0&3
\end{bmatrix}\\
&Row_3=Row_2+Row_3\\
&Row_4=Row_4+(3)Row_5\\
&Row_5\Longleftrightarrow Row_3\\\\
=&\;
\begin{bmatrix}
2&0&1&2&0\\
0&-1&-1&-1&1\\
0&0&-1&-1&1\\
0&0&0&1&-7\\
0&0&0&0&-3
\end{bmatrix}\\
&Row_5=Row_3+Row_5\\
&Row_4=(-3)Row_5+Row_4\\
&Row_5=Row_4+Row_5\\\\
\end{align}
$$

I now stop Gaussian elimination because I have $A$ in **upper triangular form**. There are two caveats that you must remember when using this method to find the determinant of a matrix.
1) When **generating a new row** from an existing row, the scalar multiplied by the existing row used to generate the new row must be applied to the determinant but using the **opposite operation.**
2) When **swapping rows**, you **flip the sign** of the determinant.

$$
det(A)=
\begin{vmatrix}
2&0&1&2&2\\
2&-1&0&1&1\\
0&1&2&1&2\\
-2&0&2&-2&2\\
2&0&0&1&1
\end{vmatrix}=(2)\cdot(-1)\cdot(-1)\cdot(1)\cdot(-3)=-6
$$
Since we swapped rows once, we flip the sign to get $|A| = 6$

---

### Problem 4.4
Compute the eigen spaces of

$$
A=
\begin{bmatrix}
0&-1&1&1\\
-1&1&-2&3\\
2&-1&0&0\\
1&-1&1&0
\end{bmatrix}
$$

To begin, you first must define your **characteristic polynomial** equation in order to find your **eigen values.**



---

### Problem 4.6