### Problem 6.1
Consider the following bivariate distribution $p(x,y)$ of two discrete random variables $X$ and $Y$

| X/Y   | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $x_5$ |
| ----- | ----- | ----- | ----- | ----- | ----- |
| $y_1$ | 0.01  | 0.02  | 0.03  | 0.1   | 0.1   |
| $y_2$ | 0.05  | 0.1   | 0.05  | 0.07  | 0.2   |
| $y_3$ | 0.1   | 0.05  | 0.03  | 0.05  | 0.04  |
Compute the following:
1) The marginal distributions $p(x)$ and $p(y)$
2) The conditional distributions $p(x|Y=y_1)$ and $p(y|X=x_3)$

---
### Problem 6.2
Consider a mixture of two Gaussian distributions
$$
0.4 \mathcal{N} \left(
\begin{bmatrix}
10\\2
\end{bmatrix}
\;,\;
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
\right)
+
0.6 \mathcal{N} \left(
\begin{bmatrix}
0\\0
\end{bmatrix}
\;,\;
\begin{bmatrix}
8.4&2.0\\
2.0&1.7
\end{bmatrix}
\right)
$$
Compute the following:
1) Compute the marginal distributions for each dimension
2) Compute the mean, mode, and median for each marginal distribution
3) Compute the mean and mode for the two-dimensional distribution

---
### Problem 6.3
You have written a computer program that sometimes compiles and sometimes not. You decide to model the apparent stochasticity $x$ of the compiler using a Bernoulli distribution with parameter $\mu$:
$$
p(x|\mu)=\mu^x(1-\mu)^{1-x}, \;\; x\in \{0,1\}
$$
Choose a conjugate prior for the Bernoulli likelihood and compute the posterior distribution $p(\mu|x_1,...,x_N)$.

---
### Problem 6.4
There are two bags. The first bag contains four mangos and two apples; the second bag contains four mangos and four apples. We also have a biased coin, which shows "heads" with probability 0.6  and "tails" with probability 0.4.
If the coin shows "heads" we pick a fruit at random from bag 1; otherwise we pick a fruit at random from bag 2. Your friend flips the coin, picks a fruit at random, and presents a mango.

What is the probability that the mango was picked from bag 2?
Hint: Use **Bayes' theorem**

---
### Problem 6.5
Consider the time-series model
$$
\begin{align}
x_{t+1} &\;= Ax_t+w, \;\; w\sim \mathcal{N}(0,Q)\\
y_t &\; = Cx_t+v, \;\; v \sim \mathcal{N} (0,R),
\end{align}
$$
where $w,v$ are i.i.d. Gaussian noise variables. Further, assume that $p(x_0)=\mathcal{N}(\mu_0,\sum_0)$
1) What is the form of $p(x_0, x_1, ..., x_T)$? Justify your answer (You do not have to explicitly compute the join distribution)'
2) Assume that $p(x_t|y_1,...,y_t)=\mathcal{N}(\mu_t,\sum_t)$
	1) Compute $p(x_{t+1}|y_1,...,y_t)$
	2) Compute $p(x_{t+1}, y_{t+1}| y_1,...,y_t)$
	3) At time $t+1$, we observe the value $y_{t+1}=\hat{y}$ Compute the conditional distribution $p(x_{t+1} | y_1,...,y_{t+1})$

---
### Problem 6.6
Prove the relationship in $(6.44)$, which relates the standard definition of the variance to the raw-score expression for the variance.

---
### Problem 6.7
Prove the relationship in $(6.45)$, which relates the pairwise difference between examples in a dataset with the raw-score expression for the variance.

---
### Problem 6.8
Express the Bernoulli distribution in the natural parameter form of the exponential family, see $(6.107)$.

---
### Problem 6.9
Express the Binomial distribution as an exponential family distribution. Also express the Beta distribution is an exponential family distribution. Show that the product of the Beta and the Binomial distribution is also a member of the exponential family.

---
### Problem 6.13
Given a continuous random variable $X$, with cdf $F_X(x)$, show that the random variable $Y:=F_X(X)$ is uniformly distributed (Theorem 6.15). **Probability Integral Transformation**