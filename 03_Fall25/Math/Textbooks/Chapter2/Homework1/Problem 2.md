### ✔️Problem 2.5 $\star$

Find the set $\mathcal{S}$ of all solutions in $x$ of the following inhomogeneous linear systems $Ax=b,$ where $A$ and $b$ are defined as follows:
- **(b)** $\star$
$$\tag{Q\;2.5\;b}
A=
\left[
\begin{matrix}
1&-1&0&0&1\\
1&1&0&-3&0\\
2&-1&0&1&-1\\
-1&2&0&-2&-1
\end{matrix}
\right],
\;\;\;
b=
\left[
\begin{matrix}
3\\6\\5\\-1
\end{matrix}
\right]
$$
$$\tag{Define}
\left[
\begin{matrix}
1&-1&0&0&1&&3\\
1&1&0&-3&0&&6\\
2&-1&0&1&-1&&5\\
-1&2&0&-2&-1&&-1
\end{matrix}
\right]
$$
$$\tag{Row Reduce 1}
\begin{matrix}
\left[
\begin{matrix}
1&-1&0&0&1 && 3\\
0&2&0&-3&-1 && 3\\
0&1&0&1&-3 && -1\\
0&1&0&-2&0 && 2
\end{matrix}
\right]
\\
\begin{matrix}
1)\;R_2=(-1)R_1+R_2\\
2)\;R_3=(-2)R_1+R_3\\
3)\;R_4=R_1+R_4
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 2}
\begin{matrix}
\left[
\begin{matrix}
1&0&0&-2&1 && 5\\
0&1&0&-2&0 && 2 \\
0&2&0&-3&-1 && 3\\
3&-2&0&1&0 && -8
\end{matrix}
\right]
\\
\begin{matrix}
1)\;R_3=R_3+3(R_1)\\
2)\;R_1=R_4+R_1 \\
3)\;R_4\Longleftrightarrow R_2
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 3}
\begin{matrix}
\left[
\begin{matrix}
1&0&0&-2&1 && 5\\
0&1&0&-2&0 && 2 \\
0&0&0&1&-1 && -1\\
0&0&0&3&-3 && -19
\end{matrix}
\right]
\\
\begin{matrix}
1)\;R_4=(-3)R_1+R_4\\
2)\;R_4=(2)R_2+R_4\\
3)\;R_3=(-2)R_2+R_3
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 4}
\begin{matrix}
\left[
\begin{matrix}
1&0&0&-2&1 && 5\\
0&1&0&-2&0 && 2 \\
0&0&0&1&-1 && -1\\
0&0&0&0&0 && 0
\end{matrix}
\right]
\\
\begin{matrix}
1)\;R_4=(-1)R_3+R_4\\
2)\;R_4=\frac{1}{2}R_4=\\
3)\;R_4=(-1)R_3+R_4
\end{matrix}
\end{matrix}$$

$$\tag{Solution}
\begin{matrix}
\begin{matrix}
\begin{matrix}
x_1-2x_4+x_5=5\\
x_2-2x_4=2\\
x_4-3x_5=-1
\end{matrix}
\Longrightarrow
\begin{matrix}
x_1=3+5t\\
x_2=6t\\
x_3=s\\
x_4=-1+3t\\
x_5=t
\end{matrix}
\end{matrix}
\\\\
\text{The Solution Set:}
\\
\{(x_1,x_2,x_3,x_4,x_5)=(3+5t,6t,s,-1+3t,t):s,t\in\mathbb{R}\}
\end{matrix}
$$

