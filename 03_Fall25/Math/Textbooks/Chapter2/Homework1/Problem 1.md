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
		3) **Neutral element**: $\exists \; e\in \mathcal{g} \;\forall\; x \in \mathcal{G} : x \otimes r = x \text{ and } e\otimes x=x$
		4) **Inverse element**: $\forall\; x \in \mathcal{G} \; \exists \; y \in \mathcal{G} : x\otimes y = e \text{ and } y \otimes x=e, \text{ where } e$ is the neutral element. We often write $x^{-1}$ to denote the inverse element of $x$.

 **Closure:** 
	- To check for **closure** we check for: $x\otimes y \in\mathcal{g}$
$$\tag{Define}A(x_1,y_1,z_1)\cdot A(x_2,y_2,z_2)\Rightarrow$$
$$\tag{Matrix Mult} 
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

Furthermore, we know:
$$\tag{Proof}\begin{matrix}
&x,y,z\in\mathbb{R}\therefore
\\
x_1+x_2\in\mathbb{R} & y_1+y_2\in\mathbb{R} & z_1+z_2+x_zy_2\in\mathbb{R}
\end{matrix}$$
**Associativity:** 
	- To check for **associativity** we check for: $(x\otimes y)\otimes z=x\otimes (y\otimes z)$
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
 **Neutral Element:**
 - To check for the Neutral element we check for: $x\otimes r=x \text{ and } e\otimes x=x$
	- Consider $e=\mathbb{I}^3$ . Thus both $e \text{ and } A \in \mathcal{G}$. Since $e=\mathbb{I}$ we know $A \cdot e = A \text{ and } e \cdot A = A \therefore$ we can conclude that $\mathcal{G}$ contains the Neutral Element. 


 **Inverse Element:**
- To check for the Inverse Element we check for  $x\otimes y=e \text{ and } y\otimes x=e, \text{ where } e\rightarrow\text{ neutral element}$
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
Then we can conclude that $\mathcal{G}$ contains the **Inverse Element**
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
