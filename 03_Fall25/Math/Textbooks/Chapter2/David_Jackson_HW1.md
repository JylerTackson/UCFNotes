### ✔️Problem 2.3 $\star$
Consider the set $\mathcal{G}_{3\times3}$:
$$
\mathcal{G} \Biggl\{ =
\left[
\begin{matrix}
1 & x & z \\
0 & 1 & y \\
0 & 0 & 1
\end{matrix}
\right]
\in
\mathbb{R}^{(3\times3)}
\;\;|\;\;
x,y,z \in \mathbb{R}
\Biggl\}

$$
We define $\cdot$ as the standard matrix multiplication. Is $(\mathcal{G}, \cdot)$ a group? If yes, is it Abelian? 

To show that $(\mathcal{G},\cdot)$ is a group and Abelian, I will firstly **(1)** show that it is a group, and secondly **(2)** Show that it is an Abelian group.

1) Show that $(\mathcal{G},\cdot)$ is a group:
	- This is a 4 step process:
		1) **Closure** of $\mathcal{G}$ under $\otimes:\forall x, y\in \mathcal{G}: x\otimes y \in \mathcal{G}$
		2) **Associativity**: $\forall x, y, z\in \mathcal{G}: (x\otimes y)\otimes z = x \otimes (y \otimes z)$
		3) **Neutral** element: $\exists \; e\in \mathcal{g} \;\forall\; x \in \mathcal{G} : x \otimes r = x \text{ and } e\otimes x=x$
		4) **Inverse** element: $\forall\; x \in \mathcal{G} \; \exists \; y \in \mathcal{G} : x\otimes y = e \text{ and } y \otimes x=e, \text{ where } e$ is the neutral element. We often write $x^{-1}$ to denote the inverse element of $x$.

	1) **Closure:** $x\otimes y \in\mathcal{g}$$$\tag{Define}A(x_1,y_1,z_1)\cdot A(x_2,y_2,z_2)\Rightarrow$$$$\tag{Matrix Mult} 
			\begin{matrix}
			\Biggl(\begin{matrix}
			1&x_1&z_1\\
			0&1&y_1\\
			0&0&1
			\end{matrix}\Biggl)
			\Biggl(\begin{matrix}
			1&x_2&z_2\\
			0&1&y_2\\
			0&0&1\end{matrix}\Biggl)
			\\
			\Downarrow
			\\
			\Biggl[
			\begin{matrix}
			1&x_1+x_2&z_1+z_2+x_zy_2\\
			0&1&y_1+y_2\\
			0&0&1
			\end{matrix}
			\Biggl]
			\end{matrix}$$
		- Furthermore, we know:
$$\tag{Proof}\begin{matrix}
&x,y,z\in\mathbb{R}\therefore
\\
x_1+x_2\in\mathbb{R} & y_1+y_2\in\mathbb{R} & z_1+z_2+x_zy_2\in\mathbb{R}
\end{matrix}$$
	2) **Associativity:** $(x\otimes y)\otimes z=x\otimes (y\otimes z)$ 
		$$\tag{Define}
		\begin{matrix}
		(x\cdot y)\cdot z
		\\
		(A(x_1,y_1,z_1)\cdot A(x_2,y_2,z_2))\cdot A(x_2,y_2,z_2)\Rightarrow
		\end{matrix}$$
		$$\tag{Matrix Mult} 
			\begin{matrix}
			\Biggl(
			\Biggl[\begin{matrix}
			1&x_1&z_1\\
			0&1&y_1\\
			0&0&1
			\end{matrix}\Biggl]
			\Biggl[\begin{matrix}
			1&x_2&z_2\\
			0&1&y_2\\
			0&0&1\end{matrix}\Biggl]
			\Biggl)
			\Biggl[\begin{matrix}
			1&x_2&z_2\\
			0&1&y_2\\
			0&0&1\end{matrix}\Biggl]
			\\
			\Downarrow
			\\
			\Biggl[
			\begin{matrix}
			1&x_1+x_2&x_1y_2+z_1+z_2\\
			0&1&y_1+y_2\\
			0&0&1
			\end{matrix}
			\Biggl]
			\Biggl[
			\begin{matrix}
			1&x_1&z_3\\
			0&1&y_3\\
			0&0&1
			\end{matrix}
			\Biggl]
			\\
			\Downarrow
			\\
			\Biggl[
			\begin{matrix}
			1&x_1+x_2+x_3&x_1y_2+(x_1+x_2)y_3+z_1+z_2+z_3\\
			0&1&y_1+y_2+y_3\\
			0&0&1
			\end{matrix}
			\Biggl]
			\end{matrix}$$
		$$\tag{Define}
		\begin{matrix}
		x\cdot(y\cdot z)
		\\
		A(x_1,y_1,z_1)\cdot
		(A(x_2,y_2,z_2)\cdot A(x_3,y_3,z_3)) \Rightarrow
		\end{matrix}$$
		$$\tag{Matrix Mult} 
		
			\begin{matrix}
			\Biggl[\begin{matrix}
			1&x_1&z_1\\
			0&1&y_1\\
			0&0&1\end{matrix}\Biggl]
			\Biggl(
			\Biggl[\begin{matrix}
			1&x_2&z_2\\
			0&1&y_2\\
			0&0&1
			\end{matrix}\Biggl]
			\Biggl[\begin{matrix}
			1&x_3&z_3\\
			0&1&y_3\\
			0&0&1\end{matrix}\Biggl]
			\Biggl)
			\\
			\Downarrow
			\\
						\Biggl[
			\begin{matrix}
			1&x_1&z_1\\
			0&1&y_1\\
			0&0&1
			\end{matrix}
			\Biggl]
			\Biggl[
			\begin{matrix}
			1&x_2+x_3&x_2y_3+z_2+z_3\\
			0&1&2y_3\\
			0&0&1
			\end{matrix}
			\Biggl]
			\\
			\Downarrow
			\\
			\Biggl[
			\begin{matrix}
			1&2(x_2+x_3)&z_2y_3+z_2+z_3\\
			0&1&2y_3\\
			0&0&1
			\end{matrix}
			\Biggl]
			\end{matrix}
		$$



	3) **Neutral Element:** $x\otimes r=x \text{ and } e\otimes x=x$
		- Consider $e=\mathbb{I}^3$ . Thus both $e \text{ and } A \in \mathcal{G}$. Since $e=\mathbb{I}$ we know $A \cdot e = A \text{ and } e \cdot A = A \therefore$ we can conclude that $\mathcal{G}$ contains the Neutral Element. 


	4) **Inverse Element:** $x\otimes y=e \text{ and } y\otimes x=e, \text{ where } e\rightarrow\text{ neutral element}$
		$$\tag{Define}
		A=\left[
		\begin{matrix}
		1&x_1&z_1\\
		0&1&y_1\\
		0&0&0
		\end{matrix}
		\right]$$
		Solving for the inverse of $A$ provides us with the result:
		$$\tag{Inverse}
		A=\left[
		\begin{matrix}
		1&-x_1&x_1y_1-z_1\\
		0&1&-y_1\\
		0&0&0
		\end{matrix}
		\right]$$
$$
\begin{matrix}
\text{Since we know:}
\\
\begin{matrix}
-x_1\in\mathcal{G}\\
x_1y_1-z_1\in\mathcal{G}\\
-y_1\in\mathcal{G}
\end{matrix}
&

\end{matrix}$$
		- Then we can conclude that $\mathcal{G}$ contains the **Inverse Element**

Finally, now that I have shown it is a group, we can show that the group is Abelian.

3) Show that $(G,\cdot)$ is Abelian
	- If additionally $\forall x, y \in \mathcal{G} : x\otimes y=y\otimes x$ then $G=(\mathcal{G},\otimes)$ is an *Abelian* group **(commutative)**.

		I can disprove, the first example I tried within wolfram showed that this was false:
$$
\tag{Define}
\begin{matrix}
A=
\left[
\begin{matrix}
1&1&1\\
0&1&2\\
0&0&1
\end{matrix}
\right]
&&
B=
\left[
\begin{matrix}
1&1&5\\
0&1&3\\
0&0&1
\end{matrix}
\right]
\end{matrix}
$$
$$
\begin{matrix}
A\cdot B=
\left[
\begin{matrix}
1&1&1\\
0&1&2\\
0&0&1
\end{matrix}
\right]
\cdot
\left[
\begin{matrix}
1&1&5\\
0&1&3\\
0&0&1
\end{matrix}
\right]
=
\left[
\begin{matrix}
1&2&9\\
0&1&5\\
0&0&1
\end{matrix}
\right]
\\\\
B\cdot A=
\left[
\begin{matrix}
1&1&5\\
0&1&3\\
0&0&1
\end{matrix}
\right]
\cdot
\left[
\begin{matrix}
1&1&1\\
0&1&2\\
0&0&1
\end{matrix}
\right]
=
\left[
\begin{matrix}
1&2&8\\
0&1&5\\
0&0&1
\end{matrix}
\right]
\\\\
\therefore A \cdot B \neq B \cdot A
\end{matrix}
$$


---

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


---

### ✔️Problem 2.8 $\star$
Determine the inverses of the following matrices if possible:
- **(b)** $\star$ Find the inverse matrix of $A$
$$
\tag{Q\;2.8\;b}
A=\left[
\begin{matrix}
1&0&1&0\\
0&1&1&0\\
1&1&0&1\\
1&1&1&0
\end{matrix}\right]
$$
$$
\tag{Row Reduce 1}
\left[
\begin{matrix}
\begin{matrix}
1&0&1&0\\
0&1&1&0\\
1&1&0&1\\
1&1&1&0
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
1&0&0&0\\
0&1&0&0\\
0&0&1&0\\
0&0&0&1
\end{matrix}
\end{matrix}
\right]
$$
$$
\tag{Row Reduce 2}
\begin{matrix}
\left[
\begin{matrix}
\begin{matrix}
1&0&1&0\\
0&1&1&0\\
0&1&-1&1\\
0&1&0&0
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
1&0&0&0\\
0&1&0&0\\
-1&0&1&0\\
-1&0&0&1
\end{matrix}
\end{matrix}
\right]
\\
1) R_3=(-1)R_1+R_3\\
2) R_4=(-1)R_1+R_4
\end{matrix}
$$
$$
\tag{Row Reduce 3}
\begin{matrix}
\left[
\begin{matrix}
\begin{matrix}
1&0&1&0\\
0&1&1&0\\
0&0&-1&0\\
0&0&-2&1
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
1&0&0&0\\
0&1&0&0\\
-1&-1&0&1\\
-1&-1&1&0
\end{matrix}
\end{matrix}
\right]
\\
3) R_3=(-1)R_2+R_3\\
4) R_4=(-1)R_2+R_4\\
5) R_3\Longleftrightarrow R_4
\end{matrix}
$$
$$
\tag{Row Reduce 4}
\begin{matrix}
\left[
\begin{matrix}
\begin{matrix}
1&0&0&0\\
0&1&0&0\\
0&0&1&0\\
0&0&0&1
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
0&-1&0&1\\
-1&0&0&1\\
1&1&0&-1\\
1&1&1&-2
\end{matrix}
\end{matrix}
\right]
\\
6) R_1=R_3+R_1\\
7) R_2=R_3+R_2\\
8) R_4=(-2)R_3+R_4\\
9) R_3=(-1)R_3\\\\
\therefore
\end{matrix}
$$
$$\tag{A\;2.8\;b}
\begin{matrix}
\text{The inverse matrix}
\\\\
A^{-1}=
\left[
\begin{matrix}
0&-1&0&1\\
-1&0&0&1\\
1&1&0&-1\\
1&1&1&-2
\end{matrix}
\right]

\end{matrix}
$$

---

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


---

### ✔️Problem 2.12 $\star$
Consider two subspaces of $\mathbb{R}^4:$
$$\tag{Q\;2.12}
U_1=span[\left[\begin{matrix}1\\1\\-3\\1\end{matrix}\right],
\left[\begin{matrix}2\\-1\\0\\-1\end{matrix}\right],
\left[\begin{matrix}-1\\1\\-1\\1\end{matrix}\right]
], \;\;\;\;\;\;\;
U_2=span[\left[\begin{matrix}-1\\-2\\2\\1\end{matrix}\right],
\left[\begin{matrix}2\\-2\\0\\0\end{matrix}\right],
\left[\begin{matrix}-3\\6\\-2\\-1\end{matrix}\right]
]
$$
Determine a basis of $U_1\cap U_2$

**I will do this by:**
- **(1)** Express $U_1 = \text{Col}(A), U_2 = \text{Col}(B)$.
- (2) Solve $Ax=By$.
- (3) The solutions give you the intersection space.
- (4) Compute a basis by picking independent vectors.

- **(a)** Express $U_1 = \text{Col}(A), U_2 = \text{Col}(B)$.
$$
U_1=\left[
\begin{matrix}
1&2&-1\\
1&-1&1\\
-3&0&-1\\
1&-1&1
\end{matrix}
\right]
\Longrightarrow
\left[
\begin{matrix}
1&0&\frac{1}{3}\\
0&1&\frac{-2}{3}\\
0&0&0\\
0&0&0
\end{matrix}
\right]
\Longrightarrow
\text{Col}(A)=
\left[
\begin{matrix}
\left[
\begin{matrix}
1\\1\\-3\\1
\end{matrix}
\right],
&
\left[
\begin{matrix}
2\\-1\\0\\-1
\end{matrix}
\right]
\end{matrix}
\right]
$$
$$
U_2=\left[
\begin{matrix}
-1&2&-3\\
-2&-2&6\\
2&0&-2\\
1&0&-1
\end{matrix}
\right]
\Longrightarrow
\left[
\begin{matrix}
1&0&-1\\
0&1&-2\\
0&0&0\\
0&0&0
\end{matrix}
\right]
\Longrightarrow
\text{Col}(B)=
\left[
\begin{matrix}
\left[
\begin{matrix}
-1\\-2\\2\\1
\end{matrix}
\right],
&
\left[
\begin{matrix}
2\\-2\\0\\0
\end{matrix}
\right]
\end{matrix}
\right]
$$

- **(b)** Solve $Ax=By$
Vectors that lie in both subspaces are precisely those of the form:
$$
w=Ax=By\Longleftrightarrow Ax-By=0
$$
So form the block matrix :
$$
M=[A\;\;\;-B]\;\;\;\text{ and solve }\;\;\;M\left[\begin{matrix}x\\y\end{matrix}\right]=0
$$
- **(c)** Intersection Space
This creates:
$$
M=
\left[
\begin{matrix}
1&2&-1&2\\
1&-1&-2&-2\\
-3&0&2&0\\
1&-1&1&0
\end{matrix}
\right]

$$
- **(d)** Compute basis
Where we can compute:
$$
M\Longrightarrow
\left[
\begin{matrix}
1&0&0&\frac{4}{9}\\
0&1&0&\frac{10}{9}\\
0&0&1&\frac{2}{3}\\
0&0&0&0
\end{matrix}
\right]$$
$\therefore$ means that the basis of $U_1 \cap U_2$ is:
$$
M_{(BASIS)}=\{x_1,\;x_2,\;x_3\}=
\left[
\begin{matrix}
\left[
\begin{matrix}
1\\1\\-3\\1
\end{matrix}
\right],
&
\left[
\begin{matrix}
2\\-1\\0\\-1
\end{matrix}
\right],
&
\left[
\begin{matrix}
-1\\-2\\2\\1
\end{matrix}
\right]
\end{matrix}
\right]
$$

---

### ✔️Problem 2.16 $\star$
Are the following mappings linear?
According to the definition provided by the book, if a mapping is linear it preserves the following:
$$
\tag{Definition}
\begin{matrix}
\begin{matrix}
\text{Vector Addition } (2.85)\\
\Phi(x+y)=\Phi(x)+\Phi(y)
\end{matrix}
&&
\begin{matrix}
\text{Scalar Multiplication } (2.86)\\
\Phi(\lambda x)=\lambda \Phi (x)
\end{matrix}
\end{matrix}
$$

- $^\star$**(a)** Let $a,b\in \mathbb{R}$
$$\tag{Q\;2.16\;a}\begin{matrix}
\Phi:L^1([a,b])\to\mathbb{R}
\\
f\rightarrowtail\Phi(f)=\int^{b}_{a}f(x)dx,
\end{matrix}
$$	where $L^1([a,b])$ denotes the set of integrable functions on $[a,b]$

- **Vector Addition (2.85)**
	We know: 
	$$\tag{Define}\Phi(f)=\int^{b}_{a}f(x)dx$$
	$\therefore$ if we try:
	$$\tag{Add}\Phi(f+g)=\int^{b}_{a}(f(x)+g(x))dx=\int^{b}_{a}f(x)dx+\int^{b}_{a}g(x)dx=\Phi(f)+\Phi(g)$$
	$\therefore \Phi$ holds under Vector Addition.

- **Scalar Multiplication (2.86)**
	We know:
$$
\tag{Define}
\Phi(f)=\int^{b}_{a}f(x)dx
$$
	$\therefore$ if we try:
$$\tag{Mult}\Phi(\lambda f)=\int^{b}_{a}\lambda f(x)dx=\lambda\int^{b}_{a}f(x)dx=\lambda\Phi(f)$$
	$\therefore$ $\Phi$ holds under Scalar Multiplication


Since both **Vector Addition** and **Scalar Multiplication** are **properties** of $\Phi$ we can say that **$\mathbf{\Phi}$ is a linear mapping**.

- $^\star$**(b)** 
$$\tag{Q\;2.16\;b}
\begin{matrix}
\Phi:C^1\to C^0
\\
f\rightarrowtail\Phi(f)=f^\prime
\end{matrix}$$
Where for $k \geq 1, C^k$ denotes the set of $k$ times continuously differentiable functions, and $C^0$ denotes the set of continuous functions.

- **Vector Addition (2.85)**
	We know: 
	$$\tag{Define}\Phi(f)=f^\prime$$
	$\therefore$ if we try:
	$$\tag{Add}\Phi(f+g)=f^\prime+g^\prime=\Phi(f)+\Phi(g)$$
	$\therefore \Phi$ holds under Vector Addition.

- **Scalar Multiplication (2.86)**
	We know:
$$
\tag{Define}
\Phi(f)=f^\prime
$$
	$\therefore$ if we try:
$$\tag{Mult}\Phi(\lambda f)=\lambda f^\prime=\lambda\Phi(f)$$
	$\therefore$ $\Phi$ holds under Scalar Multiplication


Since both **Vector Addition** and **Scalar Multiplication** are **properties** of $\Phi$ we can say that **$\mathbf{\Phi}$ is a linear mapping**.



- $^\star$**(c)**
$$
\tag{Q\;2.16\;c}
\begin{matrix}
\Phi:\mathbb{R}\to\mathbb{R}
\\
x\rightarrowtail\Phi(x)=cos(x)
\end{matrix}$$
- **Vector Addition (2.85)**
	We know: 
	$$\tag{Define}\Phi(x)=cos(x)$$
	$\therefore$ if we try:
	$$\tag{Add}\Phi(f+g)=cos(f+g)\neq cos(f)+cos(g)$$$$\Phi(f+g)\neq\Phi(f)+\Phi(g)$$
	$\therefore \Phi$ does not hold under Vector Addition.

Since **Vector Addition** does not hold $\mathbf{\Phi}$ is **not** a **linear mapping**.

---
### ✔️Problem 2.17 $\star$
Consider the linear mapping
$$
\tag{Q\;2.17}
\begin{matrix}
\Phi:\mathbb{R}^3\to\mathbb{R}^4
\\
\Phi \Bigg(\left[\begin{matrix}
x_1\\x_2\\x_3
\end{matrix}\right]\Bigg)=
\left[
\begin{matrix}
3x_1+2x_2+x_3\\
x_1+x_2+x_3\\
x_1-3x_2\\
2x_1+3x_2+x_3
\end{matrix}\right]
\end{matrix}
$$
- **(a)** Find the transformation matrix $A_{\Phi}$
The matrix $A$ of $\Phi:\mathbb{R}^3\to\mathbb{R}^4$ shown below is the transformation matrix:
$$\tag{A 2.17 a}
A=\left[
\begin{matrix}
3x_1+2x_2+x_3\\
x_1+x_2+x_3\\
x_1-3x_2\\
2x_1+3x_2+x_3
\end{matrix}\right]\Longrightarrow\left[
\begin{matrix}
3&2&1\\
1&1&1\\
1&-3&0\\
2&3&1
\end{matrix}
\right]
$$
- **(b)** Determine $rk(A_{\Phi})$
The rank of a matrix is the number of linearly independent columns.
$$
\tag{Row Reduce}
A=
\left[
\begin{matrix}
3&2&1\\
1&1&1\\
1&-3&0\\
2&3&1
\end{matrix}
\right]
=
\left[
\begin{matrix}
1&0&0\\
0&1&0\\
0&0&1\\
0&0&0
\end{matrix}
\right]
$$
$\therefore$ the $rk(A_\Phi)=3$
- **(c)** Compute the kernel and image of $\Phi$. What are $dim(ker(\Phi))$ and $dim(Im(\Phi))$
	- Kernel = $Null(\Phi)$
		- Since $A$ is linearly independent, $nullity =0 \therefore ker(\Phi)=0$
	- Image $=rank + nullity=$ number of col's
		- $Im(\Phi)=3+0=3$

	- $dim(ker\Phi))=0$
	- $dim(Im(\Phi))=3$
---