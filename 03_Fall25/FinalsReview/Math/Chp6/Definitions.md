### Important Notation
1) $\Omega\to$ **Sample space**
	- The sample space is the set of of all possible outcomes.
2) $\mathcal{A}\to$ **Event Space**
	- The event space is the space of potential results. The event space is obtained by considering the collection of subsets of the sample space.
		- $\mathcal{A}$ is often the power set of $\Omega$
3) $P\to$ **Probability**
	- The measure of the probability, or degree of belief, in which even $P(x)$ will occur.
4) $\mathcal{T}\to$ **Target Space**
	- Rather than referring to the probability space, we refer to the target space. We refer to $\mathcal{T}$ as the target space and the elements of $\mathcal{T}$ as the states.
5) $X\to$ **Random Variable**
	- The function $\Omega\to\mathcal{T}$ takes an element of $\Omega$ and returns a state in $\mathcal{T}$; the mapping from $\Omega\to\mathcal{T}$ is known as the *random variable.*

---
### Formula - Joint Probability
We define the **joint probability** as the entry of both values jointly:
$$
P(X=x_i,Y=y_i)=\frac{n_{ij}}{N}
$$
Where $n_{ij}$ is the number of events with state $x_i$ and $y_j$ and $N$ is the total number of events.

---
### Formula - Marginal Probability
We define the **marginal probability** as the probability of a single variable taking a specific value, obtained by summing over all possible states of the other variable:
$$
P(X=x_i)=\sum_{j}P(X=x_i,Y=y_j)=\frac{\sum_j n_{ij}}{N}
$$
---
### Formula - Conditional Probability
We define the **conditional probability** as the probability of one variable taking a specific value given that the other variable is observed in a particular state:
$$
P(X=x_i|Y=y_j)=\frac{P(X=x_i,Y=y_j)}{P(Y=y_j)}=\frac{n_{ij}}{\sum_{i^\prime}n_{i^\prime j}}
$$
Where $i^\prime$ is being used to denote the difference between $i\Longleftrightarrow i^\prime$

---
### Definition 6.1 - Probability Density Function
A function $f:\mathbb{R}^D\to\mathbb{R}$ is called a *probability density function* (pdf) if:
1) $\forall x\in\mathbb{R}^D:f(x)\geq 0$
2) Its integral exists and
$$
\int_{\mathbb{R}^D} f(x) dx=1
$$---
### Definition 6.2 - Cumulative Distribution Function
A *cumulative distribution function* (cdf) of a multivariate real-valued random variable $X$ with states $x\in\mathbb{R}^D$ is given by:
$$
F_X(x)=P(X_1\leq x_1,...,X_D\leq x_D)
$$
The cdf can be expressed also as the integral of the probability density function $f(x)$ s.t.:
$$
F_X(x)=\int^{x_1}_{-\infty} ... \int^{x_D}_{-\infty} f(z_1,...,z_D)dz_1 ... dz_D
$$
---
### Rule - Sum Rule
$$
p(x)=
\begin{cases}
\sum_{y\in\mathcal{Y}} p(x,y) \;\;\;\; \text{if }y \text{ is discrete}\\\\
\int_\mathcal{Y} p(x,y)dy \;\;\;\; \text{if }y \text{ is continuous}
\end{cases}
$$
Where $\mathcal{Y}$ are the states of the target space of the random variable $Y$.
#### Marginalization property
The sum rule relates the joint distribution to a marginal distribution. When the joint distribution contains more than two random variables, the sum rule can be applied to any subset of random variables resulting in a marginal distribution of potentially more than one random variable. This leads to the marginal:
$$
p(x_i)=\int p(x_1,...,x_D)dx_{\textbackslash i}
$$
Where by repeated application of the sum rule where we sum out all random variables except $x_i$, denoted by the $x_{\textbackslash i}$ read "all except i".

---
### Rule - Product Rule
The product rules relates the joint distribution to the conditional distribution using:
$$
p(x,y)=p(y|x)p(x)
$$
This formula above is expressed in terms for **discrete random variables** using the probability mass functions. If we want to use this rule expressed int terms for **continuous random variables** we must use the probability density function shown several rules above.

---
### Rule - Bayes' Rule
Assuming we have some prior knowledge such as $p(x)$ and some relationship $p(y|x)$; if we observe $y$, we can use Bayes' theorem to draw some conclusion about $x$ given the observed values of $y$.
$$
\underbrace{p(x \mid y)}_{\text{posterior}}
=
\frac{
    \overbrace{p(y \mid x)}^{\text{likelihood}}
    \;\;
    \overbrace{p(x)}^{\text{prior}}
}{
    \underbrace{p(y)}_{\text{evidence}}
}.
$$
Bayes' rule is a direct consequence of the product rule shown within $(6.22)$ since the order within the product rule does not matter.

---
### Definition 6.3 - Expected Value
The expected value of a function $g:\mathbb{R}\to\mathbb{R}$ of a univariate **continuous** random variable $X\sim p(x)$ is given by:
$$
\mathbb{E}_X[g(x)]=\int_\mathcal{X} g(x) p(x)dx
$$
Furthermore, the expected value of a function $g$ of a discrete random variable $X\sim p(x)$ is given by:
$$
\mathbb{E}_X[g(x)]=\sum_{x\in\mathcal{X}} g(x)p(x)
$$
Where in both of these $\mathcal{X}$ is the target space of the random variable $X$.

---
### Definition 6.4 - Mean
The mean of a random variable $X$ with states $x\in \mathbb{R}^D$ is an average and is defined as:
$$
\mathbb{E}_X[x]=
\begin{bmatrix}
\mathbb{E}_{X_1}[x_1]\\
\vdots\\
\mathbb{E}_{X_D}[x_D]
\end{bmatrix}\in\mathbb{R}^D
$$
where
$$
\mathbb{E}_{X_d}[x_d] :=
\begin{cases}
\int_\mathcal{X} x_d p(x_d) dx_d \;\;\; \text{if } X \text{ is a continous random variable} \\\\
\sum_{x_i\in\mathcal{X}} x_i p (x_d = x_i) \;\;\; \text{if } X \text{ is a discrete random variable}
\end{cases}
$$
---
### Definition 6.5 - Covariance 
Covariance is the measure of how two random variables change together. If their covariance is positive the variables tend to change in the same direction while if it is negative they will change in opposite directions. A 0 covariance indicates no linear relationship between their movements.

#### Univariate
The covariance between two univariate random variables $X,Y\in\mathbb{R}$ is given by the expected product of the deviations from their respective means:
$$
\text{Cov}_{X,Y} [x,y] := \mathbb{E}_{X,Y}\left[ (x-\mathbb{E}_X[x]) (y-\mathbb{E}_Y[y]) \right]
$$
By using the linearity of expectations we can rewrite the expression above as:
$$
\text{Cov}[x,y]=\mathbb{E}[xy]-\mathbb{E}[x]\mathbb{E}[y]
$$
#### Multivariate
The covariance between two multivariate random variables $X$ and $Y$ can be written as:
$$
\text{Cov}[x,y] = \mathbb{E}[xy^\top] - \mathbb{E}[x] \mathbb{E}[y]^\top=Cov[y,x]^\top \in\mathbb{R}^{dim(x)\times dim(y)}
$$
---
### Definition 6.7 - Variance
The variance  of a random variable $X$ with states $x\in\mathbb{R}^D$ and a mean vector $\mu\in\mathbb{R}^D$ is defined as
$$
\begin{align}
\mathbb{V}_X[x]=&\;\text{Cov}_X[x,x]\\\\
=&\; \mathbb{E}_X\left[ (x-\mu)(x-\mu)^\top \right]=\mathbb{E}_X [xx^\top]-\mathbb{E}_X[x]\mathbb{E}_X[x]^\top\\\\
=&\;
\begin{bmatrix}
\operatorname{Cov}[x_1, x_1] & \operatorname{Cov}[x_1, x_2] & \cdots & \operatorname{Cov}[x_1, x_D] \\
\operatorname{Cov}[x_2, x_1] & \operatorname{Cov}[x_2, x_2] & \cdots & \operatorname{Cov}[x_2, x_D] \\
\vdots & \vdots & \ddots & \vdots \\
\operatorname{Cov}[x_D, x_1] & \cdots & \cdots & \operatorname{Cov}[x_D, x_D]
\end{bmatrix}
\end{align}
$$
---
