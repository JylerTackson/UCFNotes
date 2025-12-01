### Problem 5.1
Compute the derivative $f^\prime(x)$ for:
$$f(x)=log(x^4)sin(x^3)$$

---
### Problem 5.2
Compute the derivative $f^\prime (x)$ of the logistic sigmoid
$$
f(x) = \frac{1}{1+e^{-x}}
$$
---
### Problem 5.3
Compute the derivative $f^\prime (x)$ of the function
$$
f(x)=exp(-\frac{1}{2\sigma^2}(x-\mu)^2)
$$
where $\mu,\sigma\in\mathbb{R}$ are constants.

---
### Problem 5.4
Compute the Taylor polynomials $T_n, n=0,...,5$ of $f(x)=sin(x)+cos(x)$ at $x_0=0$

---
### Problem 5.5
Consider the following functions:
$$
\begin{matrix}
f_1(x)=sin(x_1)cos(x_2),\;\;x\in\mathbb{R}^2\\\\
f_2(x,y)=x^\top y , \;\; x,y\in\mathbb{R}^n\\\\
f_3(x)=xx^\top , \;\;x\in \mathbb{R}^n
\end{matrix}
$$
1) What are the dimensions of $\frac{\partial f_i}{\partial x}$
2) Compute the Jacobians

---
### Problem 5.6
Differentiate $f$ w.r.t $t$ and $g$ w.r.t $X$ where:
$$
\begin{matrix}
f(t)=sin(log(t^\top t)), &&t\in \mathbb{R}^D\\\\
g(X)=tr(AXB), && A\in \mathbb{R}^{D\times E}, X\in \mathbb{R}^{E\times F}, B\in \mathbb{R}^{F\times D}
\end{matrix}
$$

---
### Problem 5.7
Compute the derivatives $\frac{df}{dx}$ of the following functions by using the chain rule. Provide the dimensions of every single partial derivative. Describe steps in detail.
1) $f(z)=log(1+z),\;\; z=x^\top x, \;\; x\in \mathbb{R}^D$
2) $f(z)=sin(z), \;\; z=Ax+b, \;\; A\in\mathbb{R}^{E\times D}, \; x\in\mathbb{R}^D, b\in\mathbb{R}^E$
where sin$(\cdot)$ is applied to every element of $z$.

---
### Problem 5.8
Compute the derivatives $\frac{df}{dx}$ of the following functions. Describe your steps in detail.
1) Use the chain rule. Provide the dimensions of every single partial derivative