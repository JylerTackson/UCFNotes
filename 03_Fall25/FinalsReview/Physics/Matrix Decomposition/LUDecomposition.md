$LU$ Decomposition is a numerical method to decompose a matrix $A$ into the form:
$$
A=LU
$$
Where:
- $L\to$ is a lower triangular matrix where the diagonal elements are 1
- $U\to$ is an upper triangular matrix

$$
\begin{bmatrix}
2&1&1\\
4&3&3\\
8&7&9
\end{bmatrix}
=
\begin{bmatrix}
1&0&0\\
L_{21}&1&0\\
L_{31}&L_{32}&1
\end{bmatrix}
\begin{bmatrix}
2&1&1\\
4&3&3\\
8&7&9
\end{bmatrix}
$$
To form both $L$ and $U$ you begin by row reducing $A$.
1) $R_2 = -2(R_1)+R_2$
$$\begin{bmatrix}
2&1&1\\
4&3&3\\
8&7&9
\end{bmatrix}
\Longrightarrow
\begin{bmatrix}
2&1&1\\
0&1&1\\
8&7&9
\end{bmatrix}
$$
Now we know that:
- $L_{21}$ =$|-2|$ we know this because the value that replaces the $L_{\#\#}$ value is the absolute value of the coefficient used to row reduce $A$.
- $U$ is updated to reflect the row reduced $A$
We continue till we have all the $L_{\#\#}$ slots taken up.

1) $R_3 = -4(R_1)+R_3$
$$
\begin{bmatrix}
2&1&1\\
0&1&1\\
8&7&9
\end{bmatrix}
\Longrightarrow
\begin{bmatrix}
2&1&1\\
0&1&1\\
0&3&5
\end{bmatrix}
$$
2) $R_3 = -3(R_2)+R_3$
$$
\begin{bmatrix}
2&1&1\\
0&1&1\\
0&3&5
\end{bmatrix}
\Longrightarrow
\begin{bmatrix}
2&1&1\\
0&1&1\\
0&0&2
\end{bmatrix}
$$
We can now fully construct our $LU$ decomposition as:
$$
A=LU=
\begin{bmatrix}
1&0&0\\
2&1&0\\
4&3&1
\end{bmatrix}
\begin{bmatrix}
2&1&1\\
0&1&1\\
0&0&2
\end{bmatrix}
$$
