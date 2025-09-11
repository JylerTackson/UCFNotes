**Homework Problems:**
1) 2.3
2) 2.5b
3) 2.8b
4) 2.9
5) 2.12
6) 2.16a-c
7) 2.17

---

### ✔️Problem 2.1
We consider $(\mathbb{R}\{-1\},\star),$ where
$$\tag{Q\; 2.1}
\begin{matrix}
a\star b:=ab+a+b, &&&& a,b \in \mathbb{R}\{-1\}
\end{matrix}
$$
- (a) Show that $(\mathbb{R}\{-1\},\star)$ is an Abelian group.
In this problem, I am trying to show that my given set ($\mathbb{R}\{-1\},\star$), which is the set of all real numbers other than -1, is indeed a set by showing it follows the definition of a group: 

1) Show that $(\mathbb{R}\{-1\},\star)$ is a group
	-  **Closure** of $\mathcal{G}$ under $\otimes:\forall x, y\in \mathcal{G}: x\otimes y \in \mathcal{G}$
		- To prove closure within our group $\mathcal{G}$ we need to show that $x\otimes y\in\mathcal{G}$. Since our set is the set of real numbers, other than $\{-1\}$, there is no problem showing that $a,b \text{ \& }a\otimes b\in \mathbb{R}$. However we must show that $a\otimes b \neq -1$ 
			$$\tag{Contradiction}ab+a+b=-1$$$$\tag{Rearrange}ab+a+b+1=$$$$\tag{Factor}(a+1)(b+1)=0$$
		- For the product to be zero $\{a,b\}$ have to $=-1$, but by assumption, neither $a$ nor $b$ is allowed to be $-1$. $\therefore a\star b$ is a real number and it $\neq-1$

	-  **Associativity**: $\forall x, y, z\in \mathcal{G}: (x\otimes y)\otimes z = x \otimes (y \otimes z)$
		- To prove associativity within our group $\mathcal{G}$ we need to show that $(x\otimes y)\otimes z = x \otimes (y \otimes z)$.
		  We are trying to prove that $x\star y = xy+x+y$ is associative.

		- **(Left)**
			$$\tag{Define}x=(a\star b)=ab+a+b$$$$\tag{LH Distribute}(y\star x)=yx+y+x=y(ab+a+b)+y+(ab+a+b)$$$$\tag{Distribute}(y\star x)=yab+ya+yb+ab+y+a+b$$
		- **(Right)**
			$$\tag{Define}x=(a\star b)=ab+a+b$$$$\tag{RH Distribute}(x\star y)=xy+x+y=(ab+a+b)y+(ab+a+b)+y$$$$\tag{Distribute}(x\star y)=yab+ya+yb+ab+a+b+y$$

	-  **Neutral** element: $\exists \; e\in \mathcal{g} \;\forall\; x \in \mathcal{G} : x \otimes e = x \text{ and } e\otimes x=x$
		- To show there is a neutral element, we want to show that:$$\begin{matrix}x \otimes e = x \\\text{and}\\ e\otimes x=x\end{matrix}$$
		- $x\otimes e=x$
		$$\tag{Define}x\star e=x\;\;\Rightarrow\;\; xe+x+e=x$$$$\tag{Subtract x}xe+0+e=0$$$$\tag{Farctor e}e(x+1)=0$$
		Since we know that $x\neq-1$ $$\tag{Solution}e=0$$$$\tag{Verify}x\star (0)=x(0)+x+(0)=x$$

		- Since this is commutative, we know that $e\otimes x = x$ gives the same


	-  **Inverse** element: $\forall\; x \in \mathcal{G} \; \exists \; y \in \mathcal{G} : x\otimes y = e \text{ and } y \otimes x=e, \text{ where } e$ is the **neutral element**. We often write $x^{-1}$ to denote the inverse element of $x$.
		- To show there is a Inverse element, we want to show that:$$\begin{matrix}x^{-1}=x\otimes y = e_1=0 \\\text{and}\\ x^{-1}= y \otimes x=e_2=0\end{matrix}$$
			- We have already solved for the identity elements $e=\left[\begin{matrix}0\\0\end{matrix}\right]$ within the prior step.
		- $x\otimes y=e$$$\tag{Define} x\star y =e \;\;\Rightarrow\;\; xy+y+x=0$$$$\tag{Rearrange}y(x+1)=-x$$$$\tag{Solve}y=-\frac{x}{x+1}$$$$\tag{Verify\;1}x\star(-\frac{x}{x+1})=(x(-\frac{x}{x+1}))+x+(-\frac{x}{x+1})\Rightarrow$$$$\tag{Verify\;2}=-\frac{x^2}{x+1}+x-\frac{x}{x+1}\Rightarrow$$
		Now put everything over $x+1$ by setting $x\Rightarrow\frac{x(x+1)}{x+1}$ $$\tag{Verify\;3}=-\frac{x^2}{x+1}+\frac{x(x+1)}{x+1}-\frac{x}{x+1}\Rightarrow$$$$=\frac{-x^2+x(x+1)-x}{x+1}=\frac{-x^2+x^2+x-x}{x+1}=\frac{0}{x+1}=0$$
		- Since this is commutative, we know that $y\otimes x=e$ as well.

2) IF $(\mathbb{R}\{-1\},\star)$ is a group, show that it is Abelian.
	- **Abelian:** If additionally $\forall x, y \in \mathcal{G} : x\otimes y=y\otimes x$ then $G=(\mathcal{G},\otimes)$ is an *Abelian* group **(commutative)**.
	- To show that this is Abelian we prove that $x\otimes y=y\otimes x$$$\tag{Define}x\star y=y\star x \;\;\;\;\;\Rightarrow\;\;\;\;\; xy+x+y=yx+y+x$$
	Since $xy=yx$ and $x+y=y+x$ $$x\star y=y\star x \;\;\therefore\text{ It is an Abelian group.}$$
	- (b) Solve $$\tag{Q\; 2.1.b}3\star x\star x = 15$$
		- in the Abelian group $(\mathbb{R}\{-1\},\star),$ where $\star$ is defined above.
		- Using the isomorphism $\varphi(a)=a+1$:$$\varphi(3\star x\star x)=\varphi(3)\varphi(x)\varphi(x)=(3+1)(x+1)^2=4(x+1)^2$$
	  and $\varphi(15)=15+1=16 \; \therefore$ $$4(x+1)^2=16\;\;\;\;\Rightarrow\;\;\;\;(x+1)^2=4 \;\;\;\;\Rightarrow\;\;\;\;x+1=\pm2$$
	  Solutions (and both are $\neq-1$): $$x=1\;\;\;\; \text{ or } \;\;\;\; x=-3$$
	  Quick checks: $3\star 1 = 7, 7 \star 1 = 15.$ And $3\star (-3)=-9,(-9)\star(-3)=15$
---
### ❌Problem 2.2
Let $n$ be in $\mathbb{N}$\{0}. Let $k,x$ be in $\mathbb{Z}$. We define the congruence class $\bar{k}$ of the integer $k$ as the set
$$
\begin{matrix}
\bar{k}=\{x\in\mathbb{Z}|x-k=0\;\;(modn)\}\\
\;\;\;\;\;\;\;\;\;\; = \{x\in \mathbb{Z}| \exists a\in\mathbb{Z}:(x-k=n\cdot a)\}
\end{matrix}
$$
We now define $\mathbb{Z}/n\mathbb{Z}$ (sometimes written $\mathbb{Z}_n$) as the set of all congruence classes modulo $n$. Euclidean division implies that this set is a finite set containing $n$ elements:
$$\mathbb{Z}_n=\{\bar{0},\bar{1},...,\overline{n-1}\}$$For all $\bar{a},\bar{b}\in\mathbb{Z}_n$
$$\overline{a}\oplus\overline{b}:=\overline{a+b}$$
- **(a)** Show that $(\mathbb{Z}_n, \oplus)$ is a group. Is it Abelian?

- **(b)** We now define another operation $\otimes$ for all $\bar{a}$ and $\bar{b}$ in $\mathbb{Z}_n$ as:
$$
\bar{a}\otimes\bar{b}=\overline{a\times b}\;,
$$
	where $a\times b$ represents the usual multiplication in $\mathbb{Z}$.
	Let $n=5$. Draw the times table of the elements of $\mathbb{Z}_5$\ $\{\overline{0}\}$ under $\otimes,$ i.e., calculate the products $\bar{a} \otimes \bar{b}$ for all $\bar{a}$ and $\bar{b}$ in $\mathbb{Z}_5$\ $\{\bar{0}\}$
	Hence, show that $\mathbb{Z}_5$\ $\{\bar{0}\}$ is closed under $\otimes$ and possesses a neutral element for $\otimes$. Display the inverse of all elements in $\mathbb{Z}_5$\ $\{\bar{0}\}$ under $\otimes$.
	Conclude that ($\mathbb{Z}_5$\ $\{\bar{0}\}$) is an Abelian group.

- **(c)** Show that ($\mathbb{Z}_8$\ $\{\bar{0}\},\otimes$) is not a group.

- **(d)** We recall that the **Bezout theorem** states that two integers $a$ and $b$ are relatively prime if and only if there exists two integers $u$ and $v$ such that $au + bv = 1$. Show that ($\mathbb{Z}_n$\ $\{\overline{0}\},\otimes$) is a group if and only fi $n \in \mathbb{N}$\ $\{0\}$ is prime.

---
### ❓Problem 2.3 $\star$
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
		- 


	4) **Inverse Element:** $x\otimes y=e \text{ and } y\otimes x=e, \text{ where } e\rightarrow\text{ neutral element}$
		- 



3) Show that $(G,\cdot)$ is Abelian
	- If additionally $\forall x, y \in \mathcal{G} : x\otimes y=y\otimes x$ then $G=(\mathcal{G},\otimes)$ is an *Abelian* group **(commutative)**.


---
### ❌Problem 2.4

**Matrix Multiplication Practice**

---
### 🔄Problem 2.5 $\star$

Find the set $\mathcal{S}$ of all solutions in $x$ of the following inhomogeneous linear systems $Ax=b,$ where $A$ and $b$ are defined as follows:

- **(a)**
$$\tag{Q\;2.5\;a}
A=
\left[
\begin{matrix}
1&1&-1&-1\\
2&5&-7&-5\\
2&-1&1&3\\
5&2&-4&2
\end{matrix}
\right],
\;\;\;
b=
\left[
\begin{matrix}
1\\-2\\4\\6
\end{matrix}
\right]
$$
$$\tag{Define}
\left[
\begin{matrix}
1&1&-1&-1&& 1\\
2&5&-7&-5&& -2\\
2&-1&1&3&& 4\\
5&2&-4&2&& 6
\end{matrix}
\right]$$
$$\tag{Row Reduce 1}
\begin{matrix}
\left[
\begin{matrix}
1&1&-1&-1&& 1\\
0&3&-5&-3&& 0\\
0&-3&-1&5&& 2\\
0&-3&-9&7&& 1
\end{matrix}
\right]
\\
\begin{matrix}
R_2=(-2)R_1+R_2\\
R_3=(-2)R_1+R_3\\
R_4=(-5)R_1+R_4
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 2}
\begin{matrix}
\left[
\begin{matrix}
1&1&-1&-1&& 1\\
0&1&-3&-1&& 0\\
0&0&-6&2&& 2\\
0&0&-4&4&& 1
\end{matrix}
\right]
\\
\begin{matrix}
R_3=R_2+R_3\\
R_2=R_2+R_4\\
R_2=(-2)R_1+R_2
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 3}
\begin{matrix}
\left[
\begin{matrix}
1&1&-1&-1&& 1\\
0&1&-3&-1&& 0\\
0&0&-1&1&& \frac{1}{4}\\
0&0&-3&1&& 1
\end{matrix}
\right]
\\
\begin{matrix}
R_3 = R_3/2\\
R_4=R_4/4\\
R_4\Longleftrightarrow R_3
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 4}
\begin{matrix}
\left[
\begin{matrix}
1&1&-1&0&& \frac{3}{2}\\
0&1&-3&0&& \frac{1}{2}\\
0&0&-1&0&& -\frac{1}{4}\\
0&0&0&1&& \frac{1}{2}
\end{matrix}
\right]
\\
\begin{matrix}
R_4=-3R_3+R_4\\
R_4=(-\frac{1}{2})R_4\\
\begin{matrix}
R_1=R_1+R_4
&
R_3=R_3+(-1)R_4
&
R_2=R_2+R_4
\end{matrix}
\end{matrix}
\end{matrix}$$
$$\tag{Row Reduce 4}
\begin{matrix}
\left[
\begin{matrix}
1&0&0&0&& \frac{2}{4}\\
0&1&0&0&& \frac{5}{4}\\
0&0&1&0&& \frac{1}{4}\\
0&0&0&1&& \frac{1}{2}
\end{matrix}
\right]
\\
\begin{matrix}
R_3=R_3(-1)\\
\begin{matrix}
R_1=R_3 + R_1 && R_2=R_3+(3)R_1
\end{matrix}\\
R_1=R_1+(-1)R_2
\end{matrix}
\end{matrix}$$
$$\therefore$$
The solution vector vector $b$ for $Ax=b$ is:
$$\tag{A\;2.5\;a}
b=
\left[\begin{matrix}
\frac{2}{4}\\
\frac{5}{4}\\
\frac{1}{4}\\
\frac{1}{2}
\end{matrix}\right]$$

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
b=
\left[
\begin{matrix}
x_1\\x_2\\x_3\\x_4\\x_5
\end{matrix}
\right]
&&&
\begin{matrix}
x_1 \Rightarrow t-2x_4+5\\
x_2 \Rightarrow t-2x_4+2 \\
x_3 \Rightarrow -1 \\
x_4 \Rightarrow  \\
x_5 \Rightarrow 
\end{matrix}
\end{matrix}
\\
\text{ Where: }
\\
\begin{matrix}
x_1=[
\begin{matrix}
\end{matrix}
]
&
x_2=[
\begin{matrix}
\end{matrix}
]
&
x_3=[
\begin{matrix}
\end{matrix}
]
&
x_4=[
\begin{matrix}
\end{matrix}
]
&
x_1=[
\begin{matrix}
\end{matrix}
]
\end{matrix}
\\
\text{Let }x_5\text{ and }x_3\text{ be free paramters. Then the solution set is}
\\
(x_1,x_2,x_3,x_4,x_5)=(), \;\; s,t \in \mathbb{R}
\end{matrix}
$$


---
### ❌Problem 2.6
Using Gaussian elimination, find all solutions of the inhomogeneous equation system $Ax=b$ with:
$$\tag{Q\;2.6}
A=
\left[
\begin{matrix}
0&1&0&0&1&0\\
0&0&0&1&1&0\\
0&1&0&0&0&1
\end{matrix}
\right],
\;\;\;
b=
\left[
\begin{matrix}
2\\-1\\1
\end{matrix}
\right]
$$

---
### ❌Problem 2.7
Find all solutions in $x=\left[\begin{matrix}x_1\\ x_2\\ x_3\end{matrix}\right] \in \mathbb{R}^3$ of the equation system $Ax=12x,$ where:
$$\tag{Q\;2.7}
A=\left[
\begin{matrix}
6&4&3\\
6&0&9\\
0&8&0
\end{matrix}
\right] \text{ and } \sum_{i=1}^{3}x_i=1$$


---
### ✔️Problem 2.8 $\star$
Determine the inverses of the following matrices if possible:
- **(a)** To compute the inverse $A^{-1}$ we need to find a matrix $X$ that satisfies $AX=I$. $\therefore$ Then, $X=A^{-1}$ so we solve $AI=X$ and reduce $A$ to row echelon form.
$$\tag{Q\;2.8\;a}
A=\left[
\begin{matrix}
2&3&4\\
3&4&5\\
4&5&6
\end{matrix}
\right]$$

$$\tag{Define}
\begin{matrix}
\text{We can find the Inverse of a Matrix A using row reduction teqhniques and the idea above:}
\\
[A|I] \Longrightarrow [I|A^{-1}]
\\\\
\left[
\begin{matrix}
\begin{matrix}
2&3&4\\
3&4&5\\
4&5&6
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
1&0&0\\
0&1&0\\
0&0&1
\end{matrix}
\end{matrix}
\right]
\end{matrix}
$$
$$
\tag{Row Reduce 1}
\begin{matrix}
\left[
\begin{matrix}
\begin{matrix}
2&3&4\\
1&1&1\\
0&-1&-2
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
1&0&0\\
\frac{-2}{3}&\frac{1}{3}&\frac{1}{3}\\
-2&0&1
\end{matrix}
\end{matrix}
\right]
\\\\
R_3 = (-2)R_1+R_3\\
R_2 = R_2+R_3\\
R_2 = (\frac{1}{3})R_2
\end{matrix}
$$
$$
\tag{Row Reduce 2}
\begin{matrix}
\left[
\begin{matrix}
\begin{matrix}
1&1&1\\
0&1&2\\
0&0&0
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
\frac{-2}{3}&\frac{1}{3}&\frac{1}{3}\\
-1&0&1\\
-2&0&1
\end{matrix}
\end{matrix}
\right]
\\\\
R_1=(-2)R_2+R_1\\
R_3=R_1+R_3\\
R_1\Longleftrightarrow R_2
\\

\end{matrix}
$$
$$
\tag{Row Reduce 3}
\begin{matrix}
\left[
\begin{matrix}
\begin{matrix}
1&0&-1\\
0&1&2\\
0&0&0
\end{matrix}
&
\left|
\begin{matrix}
{}
\\
{}
\\
{}
\end{matrix}
\right.
&
\begin{matrix}
\frac{1}{3}&\frac{1}{3}&\frac{-2}{3}\\
-1&0&1\\
-2&0&1
\end{matrix}
\end{matrix}
\right]
\\\\
R_1=(-1)R_2+R_1
\\
\end{matrix}
$$


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
### 🔄Problem 2.9 $\star$
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
x\\x\\x
\end{matrix}
\right]
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
A+X=
\left[
\begin{matrix}
\lambda+x\\
\lambda+\mu^3+x\\
\lambda-\mu^3+x
\end{matrix}
\right]
\\\\
\text{We know }x,\lambda,\mu\in\mathbb{R}\therefore
\\
\begin{matrix}
\lambda+x\in\mathbb{R}\\
\lambda+\mu^3+x\in\mathbb{R}\\
\lambda-\mu^3+x\in\mathbb{R}
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
X=\left[
\begin{matrix}
x&x&x
\end{matrix}
\right]
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
AX=
\left[
\begin{matrix}
\lambda x&\lambda x& \lambda x\\
(\lambda x + \mu^3)x&(\lambda x + \mu^3)x&(\lambda x + \mu^3)x\\
(\lambda x - \mu^3)x&(\lambda x - \mu^3)x&(\lambda x - \mu^3)x
\end{matrix}
\right]
\\\\
\text{We know }x,\lambda,\mu\in\mathbb{R}\therefore
\\ A \text{ is closed under vector addition.}
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
\therefore\text{ B is a subspace of }\mathbb{R}^3
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
x\\x\\x
\end{matrix}
\right]
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
A+X=
\left[
\begin{matrix}
\lambda^2+x\\
-\lambda^2+x\\
x
\end{matrix}
\right]
\\\\
\text{We know }x,\lambda,\in\mathbb{R}\therefore
\\
\begin{matrix}
\lambda^2+x\in\mathbb{R}\\
-\lambda^2+x\in\mathbb{R}\\
x\in\mathbb{R}
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
\lambda^2\\-\lambda^2\\0
\end{matrix}
\right]
&&
X=\left[
\begin{matrix}
x&x&x
\end{matrix}
\right]
\end{matrix}
\\
\text{Where x}\in\mathbb{R}
\\\\
AX=
\left[
\begin{matrix}
\lambda^2x&\lambda^2x&\lambda^2x\\
-\lambda^2x&-\lambda^2x&-\lambda^2x\\
0&0&0
\end{matrix}
\right]
\\\\
\text{We know }x,\lambda,\in\mathbb{R}\therefore
\\
\begin{matrix}
\lambda^2\in\mathbb{R}\\
-\lambda^2\in\mathbb{R}\\
\end{matrix}
\\\\
\therefore A \text{ is closed under vector multiplication.}
\end{matrix}
$$

- Let $\gamma$ be in $\mathbb{R}$
	- $C=\{(\xi_1,\xi_2,\xi_3)\in\mathbb{R}^3|\xi_1-2\xi_2+3\xi_3=\gamma\}$


- **(d)**  $D=\{(\xi_1,\xi_2,\xi_3)\in\mathbb{R}^3\;|\;\xi_2\in\mathbb{Z}\}$

---
### ❌Problem 2.10
Are the following sets of vectors linearly independent?
- **(a)**
$$\begin{matrix}
x_1=
\left[
\begin{matrix}
2\\-1\\3
\end{matrix}
\right],
&&
x_2=
\left[
\begin{matrix}
1\\1\\-2
\end{matrix}
\right],
&&
x_3=
\left[
\begin{matrix}
3\\-3\\8
\end{matrix}
\right]
\end{matrix}$$
- **(b)**
$$\begin{matrix}
x_1=
\left[
\begin{matrix}
1\\2\\1\\0\\0
\end{matrix}
\right],
&&
x_2=
\left[
\begin{matrix}
1\\1\\0\\1\\1
\end{matrix}
\right],
&&
x_3=
\left[
\begin{matrix}
1\\0\\0\\1\\1
\end{matrix}
\right]
\end{matrix}$$

---
### ❌Problem 2.11
Write $y=\left[\begin{matrix}1\\-2\\5\end{matrix}\right]$ as a linear combination of:
$$\begin{matrix}
x_1=
\left[
\begin{matrix}
1\\1\\1
\end{matrix}
\right],
&&
x_2=
\left[
\begin{matrix}
1\\2\\3
\end{matrix}
\right],
&&
x_3=
\left[
\begin{matrix}
2\\-1\\1
\end{matrix}
\right]
\end{matrix}$$


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
### ❌Problem 2.13
Consider two subspaces $U_1$ and $U_2$, where $U_1$ is the solution space of the homogeneous equation system $A_1x=0$ and $U_2$ is the solution space of the homogeneous equation system $A_2x=0$ with
$$\tag{Q\; 2.13}
A_1=
\left[
\begin{matrix}
1&0&1\\
1&-2&-1\\
2&1&3\\
1&0&1
\end{matrix}
\right],\;\;\;\;\;
A_2=
\left[
\begin{matrix}
3&-3&0\\
1&2&3\\
7&-5&2\\
3&-1&2
\end{matrix}
\right]
$$
- **(a)** Determine the dimension of $U_1,U_2$
- **(b)** Determine bases of $U_1$ and $U_2$
- **(c)** Determine a basis of $U_1 \cap U_2$
---
### ❌Problem 2.14
Consider two subspaces $U_1$ and $U_2$, where $U_1$ is spanned by the columns of $A_1$ and $U_2$ is spanned by the columns of $A_2$ with
$$\tag{Q\;2.14}
A_1=\left[
\begin{matrix}
1&0&1\\
1&-2&-1\\
2&1&3\\
1&0&1\end{matrix}\right],
\;\;\;\;\;
A_2=\left[
\begin{matrix}
3&-3&0\\
1&2&3\\
7&-5&2\\
3&-1&2\end{matrix}\right]$$
- **(a)** Determine the dimension of $U_1$, $U_2$
- **(b)** Determine bases of $U_1$ and $U_2$
- **(c)** Determine a basis of $U_1\cap U_2$

---
### ❌Problem 2.15
Let $F=\{(x,y,z)\in\mathbb{R}^3\;|\; x+y-z=0\}$ and $G=\{(a-b,a+b,a-3b) \; | \; a,b\in \mathbb{R}\}.$
- **(a)** Show that $G$ and $G$ are subspaces of $\mathbb{R}^3$
- **(b)** Calculate $F\cap G$ without resorting to any basis vector
- **(c)** Find one basis for $F$ and one for $G$, calculate $F\cap G$ using the basis vectors previously found and check your result with the previous question.

---
### ❌Problem 2.16 $\star$
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
	$$\tag{Add}\Phi(f+g)=cos(f+g)\neq cos(f)+cos(g)$$
	$\therefore \Phi$ does not hold under Vector Addition.

Since **Vector Addition** does not hold $\mathbf{\Phi}$ is **not** a **linear mapping**.

- **(d)** 
	$$\tag{Q\;2.16\;d}
	\begin{matrix}
	\Phi:\mathbb{R}^3\to\mathbb{R}^2
	\\
	x\rightarrowtail\Phi(x)=
	\left[\begin{matrix}
	1&1&3\\
	1&4&3
	\end{matrix}\right]x
	\end{matrix}$$
- **Vector Addition (2.85)**
	We know: 
	$$\tag{Define}\Phi(x)=
	\left[\begin{matrix}
	1&1&3\\
	1&4&3
	\end{matrix}\right]x$$
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


- **(e)** Let $\theta$ be in $[0,2\pi[$ and
	$$\tag{Q\;2.16\;e}
	\begin{matrix}
	\Phi:\mathbb{R}^2\to\mathbb{R}^2
	\\
	x\rightarrowtail
	\left[
	\begin{matrix}
	cos(\theta) & sin(\theta) \\
	-sin(\theta) & cos(\theta)
	\end{matrix}
	\right]x
	\end{matrix}$$

---
### ❌Problem 2.17 $\star$
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
- Find the transformation matrix $A_{\Phi}$
- Determine $rk(A_{\Phi})$
- Compute the kernel and image of $\Phi$. What are $dim(ker(\Phi))$ and $dim(Im(\Phi))$

---
### ❌Problem 2.18
Let $E$ be a vector space. Let $f$ and $g$ be two automorphisms on $E$ such that $f \circ g=id_E$ (r.e., $f\circ g$ is the identity mapping $id_{E}$). Show that $ker(f)=ker(g\circ f), Im(g)=Im(g\circ f)$ and that $ker(f) \cap Im(g) = \{0_E\}$

---
### ❌Problem 2.19
Consider an endomorphism $\Phi: \mathbb{R}^3\to\mathbb{R}^3$ whose transformation matrix (with respect to the standard basis in $\mathbb{R}^3$) is
$$\tag{Q\;2.19}
A_{\Phi}=\left[
\begin{matrix}
1&1&0\\
1&-1&0\\
1&1&1
\end{matrix}\right]$$
- **(a)** Determine $ker(\Phi)$ and $Im(\Phi)$
- **(b)** Determine the transformation matrix $\bar{A}_{\Phi}$ with respect to the basis:
$$
B=\Bigg(\left[\begin{matrix}1\\1\\1\end{matrix}\right],\left[\begin{matrix}1\\2\\1\end{matrix}\right],\left[\begin{matrix}0\\0\\1\end{matrix}\right]\Bigg)
$$
	i.e., perform a basis change toward the new basis $B$.