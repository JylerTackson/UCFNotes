Cholesky Decomposition states that iff there is a matrix $A$ s.t $A=A^\top$ then we are able to create a **Cholesky Decomposition** s.t:
$$
\begin{align}
A=&\;LL^\top\\\\
=&\;
\begin{bmatrix}
l_{11}&0&0\\
l_{21}&l_{22}&0\\
l_{31}&l_{32}&l_{33}
\end{bmatrix}
\begin{bmatrix}
l_{11}&l_{21}&l_{31}\\
0&l_{22}&l_{32}\\
0&0&l_{33}
\end{bmatrix}\\\\
=&\;\begin{bmatrix}
(l_{11})^2&(l_{11}l_{21})&(l_{11}l_{31})\\
(l_{21}l_{11})&(l_{21})^2+(l_{22})^2&l_{21}l_{31}+l_{22}l_{32}\\
l_{31}l_{11}& l_{31}l_{21}+l_{32}l_{22}& (l_{31})^2+(l_{32})^2+(l_{33})^2
\end{bmatrix}
\end{align}
$$
Since we know that $A=LL^\top$ we can begin solving for the elements of $LL^\top$ by setting them equal to the elements of $A$.
$$
\begin{align}
l^2_{11}=a_{11} && l_{11}=\sqrt{a_{11}} \\
l^2_{22}=a_{22}-l_{21}^2 && l_{22} = \sqrt{a_{22}-l_{21}^2}\\
\vdots\;\;\;\;\;\;\;\;\;\; && \vdots\;\;\;\;\;\;\;\;\;\;\;
\end{align}
$$
Solve for all 9 indices in the decomposition.