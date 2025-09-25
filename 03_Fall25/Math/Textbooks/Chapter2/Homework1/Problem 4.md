### ✔️Problem 2.9 $\star$
Which of the following sets are subspaces of $\mathbb{R}^3$?
- To check whether something is a subspace or not it must satisfy three things:
  1) Contain the zero vector $(0,0,0)$.
  2) Be closed under vector addition.
  3) Be closed under scalar multiplication.

- **(a)**  $A=\{(\lambda,\lambda+\mu^3,\lambda-\mu^3)\;|\;\lambda,\mu\in\mathbb{R}\}$
$$\tag{Zero Vector}
\begin{matrix}
\lambda=0,\mu=0
\\
(\lambda,\lambda+\mu^3,\lambda-\mu^3)
\\
(0,0+0^3,0-0^3)=(0,0,0)
\end{matrix}
$$
$$
\tag{Vector Add}
\begin{matrix}
\begin{matrix}
A=\left[
\begin{matrix}
\lambda\\\lambda+\mu^3\\\lambda-\mu^3
\end{matrix}
\right]
&&
X=\left[
\begin{matrix}
\lambda\\\lambda+\mu^3\\\lambda-\mu^3
\end{matrix}
\right]
\end{matrix}
\\\\
A+X=
\left[
\begin{matrix}
\lambda+\lambda\\
\lambda+\mu^3+\lambda+\mu^3\\
\lambda-\mu^3+\lambda-\mu^3
\end{matrix}
\right]
\\\\
\text{We know }\lambda,\mu\in\mathbb{R}\therefore
\\
\begin{matrix}
\lambda+\lambda\in\mathbb{R}\\
\lambda+\mu^3+\lambda+\mu^3\in\mathbb{R}\\
\lambda-\mu^3+\lambda-\mu^3\in\mathbb{R}
\end{matrix}
\\\\
\therefore A \text{ is closed under vector addition.}
\end{matrix}
$$
$$
\tag{Vector Mult}
\begin{matrix}
\begin{matrix}
A=\left[
\begin{matrix}
\lambda\\\lambda+\mu^3\\\lambda-\mu^3
\end{matrix}
\right]
&&
C=x
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
C A=
\left[
\begin{matrix}
x\lambda \\
(\lambda x + \mu^3)2x\\
(\lambda x - \mu^3)2x
\end{matrix}
\right]
\\\\
\text{We can conclude:}
\\
\begin{matrix}
x\lambda \in \mathbb{R}\\
(\lambda x + \mu^3)2x \in \mathbb{R}\\
(\lambda x - \mu^3)2x \in \mathbb{R}
\end{matrix}
\\ \therefore A \text{ is closed under scalar multiplication.}
\end{matrix}
$$

- **(b)**  $B=\{(\lambda^2,-\lambda^2,0)\;|\;\lambda\in\mathbb{R}\}$
$$
\tag{Zero Vector}
\begin{matrix}
\lambda=0
\\
(\lambda^2,-\lambda^2,0)
\\
(0^2,-0^2,0)=(0,0,0)
\\
\therefore\text{ B contains }\emptyset
\end{matrix}
$$
$$
\tag{Vector Add}
\begin{matrix}
\begin{matrix}
A=\left[
\begin{matrix}
\lambda^2\\-\lambda^2\\0
\end{matrix}
\right]
&&
X=\left[
\begin{matrix}
\lambda^2\\-\lambda^2\\0
\end{matrix}
\right]
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
A+X=
\left[
\begin{matrix}
\lambda^2+\lambda^2\\
-\lambda^2-\lambda^2\\
0
\end{matrix}
\right]
\\\\
\text{We know }x,\lambda,\in\mathbb{R}\therefore
\\
\begin{matrix}
\lambda^2+\lambda^2\in\mathbb{R}\\
-\lambda^2-\lambda^2\in\mathbb{R}\\
0\in\mathbb{R}
\end{matrix}
\\\\
\therefore B \text{ is closed under vector addition.}
\end{matrix}
$$
$$
\tag{Vector Mult}
\begin{matrix}
\begin{matrix}
A=\left[
\begin{matrix}
\lambda^2\\-\lambda^2\\0
\end{matrix}
\right]
&&
C=x
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
CA=
\left[
\begin{matrix}
\lambda^2x\\-\lambda^2x\\0
\end{matrix}
\right]
\\\\
\text{We know }x,\lambda,\in\mathbb{R}\therefore
\\
\begin{matrix}
\lambda^2x\in\mathbb{R}\\
-\lambda^2x\in\mathbb{R}\\
\end{matrix}
\\\\
\therefore B \text{ is closed under scalar multiplication.}
\end{matrix}
$$

- **(c)** Let $\gamma$ be in $\mathbb{R}$
	- $C=\{(\xi_1,\xi_2,\xi_3)\in\mathbb{R}^3|\xi_1-2\xi_2+3\xi_3=\gamma\}$
$$\tag{Zero Vector}
\begin{matrix}
\xi=0
\\
(\xi_1,\xi_2,\xi_3)
\\
(0,0,0)=(0,0,0)
\\
\therefore\text{ C contains }\emptyset
\end{matrix}$$
$$
\tag{Vector Add}
\begin{matrix}
\text{We can define two vectors:}
\\
\begin{matrix}
\hat{a}=
\left[\begin{matrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{matrix}\right]
&&
\hat{b}=
\left[\begin{matrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{matrix}\right]
\end{matrix}
\\\\
\text{Perform Vector Addition:}
\\
\hat{a}+\hat{b}=
\left[
\begin{matrix}
\xi_1 + \xi_1 \\
\xi_2 + \xi_2 \\ 
\xi_3 + \xi_3
\end{matrix}
\right]
\end{matrix}
$$
$$
\tag{Vector Add}
\begin{matrix}
\hat{a}+\hat{b}=(\xi_1-2\xi_2+3\xi_3)+(\xi_1-2\xi_2+3\xi_3)=\gamma+\gamma=2\gamma
\\\\
\text{However we see that } \hat{a}+\hat{b}=2\gamma \text{ which is a contradiction} \therefore
\\
\text{C is NOT closed under Vector Addition}
\end{matrix}
$$

- **(d)**  $D=\{(\xi_1,\xi_2,\xi_3)\in\mathbb{R}^3\;|\;\xi_2\in\mathbb{Z}\}$
$$\tag{Zero Vector}
\begin{matrix}
\xi=0
\\
(\xi_1,\xi_2,\xi_3)
\\
(0,0,0)=(0,0,0)
\\
\therefore\text{ D contains }\emptyset
\end{matrix}$$
$$
\tag{Vector Add}
\begin{matrix}
\text{We can define two vectors:}
\\
\begin{matrix}
\hat{a}=
\left[\begin{matrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{matrix}\right]
&&
\hat{b}=
\left[\begin{matrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{matrix}\right]
\end{matrix}
\\\\
\text{Perform Vector Addition:}
\\
\hat{a}+\hat{b}=
\begin{matrix}
\left[
\begin{matrix}
\xi_1 + \xi_1 \\
\xi_2 + \xi_2 \\ 
\xi_3 + \xi_3
\end{matrix}
\right]
&
\Longrightarrow
&
\left[
\begin{matrix}
\xi_1 + \xi_1 \in\mathbb{R}\\
\xi_2 + \xi_2 \in\mathbb{Z}\\ 
\xi_3 + \xi_3 \in\mathbb{R}
\end{matrix}
\right]
\end{matrix}
\end{matrix}
$$
$$
\tag{Vector Add}
\begin{matrix}
\text{Since there is no violation when adding between the }\mathbb{Z} \text{ and the }\mathbb{R.}
\\
\text{D is closed under Vector Addition.}
\end{matrix}
$$
$$
\tag{Vector Mult}
\begin{matrix}
\begin{matrix}
A=\left[
\begin{matrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{matrix}
\right]
&&
C=x
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
CA=
\left[
\begin{matrix}
\xi_1 x \\ \xi_2 x \\ \xi_3 x
\end{matrix}
\right]
\\\\
\text{Since } x\in \mathbb{R} \text{ but } \xi_2\in\mathbb{Z}
\\
\text{D is not closed under Scalar Multiplication.}
\end{matrix}
$$

