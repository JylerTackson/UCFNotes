
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
\\\\
\text{Where } L^1([a,b]) \text{ denotes the set of integrable functions on } [a,b].
\end{matrix}
$$

**Vector Addition (2.85)**
- We know: 
	$$\tag{Define}\Phi(f)=\int^{b}_{a}f(x)dx$$

- $\therefore$ if we try:

$$\tag{Add}\Phi(f+g)=\int^{b}_{a}(f(x)+g(x))dx=\int^{b}_{a}f(x)dx+\int^{b}_{a}g(x)dx=\Phi(f)+\Phi(g)$$
- $\therefore \Phi$ holds under Vector Addition.

**Scalar Multiplication (2.86)**
- We know:
$$
\tag{Define}
\Phi(f)=\int^{b}_{a}f(x)dx
$$
- $\therefore$ if we try:
$$\tag{Mult}\Phi(\lambda f)=\int^{b}_{a}\lambda f(x)dx=\lambda\int^{b}_{a}f(x)dx=\lambda\Phi(f)$$	
- $\therefore$ $\Phi$ holds under Scalar Multiplication


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
