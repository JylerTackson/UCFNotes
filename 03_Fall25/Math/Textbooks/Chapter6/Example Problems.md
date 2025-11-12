### Exercises
- 6.1✔️
- 6.2✔️
- 6.5❌
- 6.6❌
- 6.7❌
- 6.10❌
- 6.12❌
---
**6.1** Consider the following bivariate distribution $p(x, y)$ of two discrete random variables $X$ and  $Y$:

| $Y \backslash X$ | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $x_5$ |
| :--------------: | :---: | :---: | :---: | :---: | :---: |
|      $y_1$       | 0.01  | 0.02  | 0.03  |  0.1  |  0.1  |
|      $y_2$       | 0.05  |  0.1  | 0.05  | 0.07  |  0.2  |
|      $y_3$       |  0.1  | 0.05  | 0.03  | 0.05  | 0.04  |

1)  **The marginal distributions $p(x)$ and $p(y)$.**
The marginal distribution is found by summing the probabilities over all the values of the variable being marginalized:
- $p(X=x_1)=P(X,y_1)+P(X,y_2)+P(X,y_3)=0.01+0.05+0.1=0.16$
- $p(X=x_2)=P(X,y_1)+P(X,y_2)+P(X,y_3)=0.02+0.1+0.05=0.17$
- $p(X=x_3)=P(X,y_1)+P(X,y_2)+P(X,y_3)=0.03+0.05+0.03=0.11$
- $p(X=x_4)=P(X,y_1)+P(X,y_2)+P(X,y_3)=0.1+0.07+0.05=0.22$
- $p(X=x_5)=P(X,y_1)+P(X,y_2)+P(X,y_3)=0.1+0.2+0.04=0.34$
We can check that the normalization condition is satisfied:
$$
\sum_{i=1}^5p(x_i)=0.16+0.17+0.11+0.22+0.34=1
$$

2)  **The conditional distributions $p(x \mid Y = y_1)$ and $p(y \mid X = x_3)$.**
To find the conditional distributions of $p(x|Y=y_1)$ we use the definition of the conditional probability:
- $p(x_1|Y=y_1)=\frac{P(X,Y)}{p(y_1)}=\frac{0.01}{0.26}\approx0.038$
- $p(x_2|Y=y_1)=\frac{P(X,Y)}{p(y_1)}=\frac{0.02}{0.26}\approx0.077$
- $p(x_3|Y=y_1)=\frac{P(X,Y)}{p(y_1)}=\frac{0.03}{0.26}\approx0.115$
- $p(x_4|Y=y_1)=\frac{P(X,Y)}{p(y_1)}=\frac{0.1}{0.26}\approx0.385$
- $p(x_5|Y=y_1)=\frac{P(X,Y)}{p(y_1)}=\frac{0.1}{0.26}\approx0.385$

Furthermore, to find the conditional distributions of $p(y|X=x_3)$ we do:
- $p(y_1|X=x_3)=\frac{P(X,Y)}{x_3}=\frac{0.03}{0.11}\approx0.273$
- $p(y_2|X=x_3)=\frac{P(X,Y)}{x_3}=\frac{0.05}{0.11}\approx0.454$
- $p(y_3|X=x_3)=\frac{P(X,Y)}{x_3}=\frac{0.03}{0.11}\approx0.273$

---

**6.2** Consider a mixture of two Gaussian distributions (illustrated in Figure 6.4),

$$p(x,y)=0.4\mathcal{N}\left(x,y|\begin{bmatrix} 10 \\ 2 \end{bmatrix}, \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}\right) + 0.6\mathcal{N}\left(x,y|\begin{bmatrix} 0 \\ 0 \end{bmatrix}, \begin{bmatrix} 8.4 & 2.0 \\ 2.0 & 1.7 \end{bmatrix}\right)$$

1. Compute the marginal distributions for each dimension.
The marginal distribution of a weighted combination of multiple distributions can be expressed as the weighted sum of their individual marginal distributions.

Formally, if  
$$p(x) = \sum_i w_i,p_i(x)$$

with weights $w_i \ge 0$ and $\sum_i w_i = 1$, then the marginal over a variable $x_j$ is  
$$p(x_j) = \sum_i w_i,p_i(x_j)$$  
where each $p_i(x_j)$ denotes the marginal of the $i^{th}$ component.

Applying these definitions we find:
- $p(x)=0.4\mathcal{N}(x|10,1)+0.6\mathcal{N}(x|0,8.4)$
- $p(y)=0.4\mathcal{N}(x|2,1)+0.6\mathcal{N}(x|0,1.7)$

2. Compute the mean, mode and median for each marginal distribution.
The mean of a weighted sum of two distributions is the weighted sum of their averages:
- $\mathbb{E}_X[x]=0.4*10+0.6*0=4$
- $\mathbb{E}_Y[y]=0.4*2+0.6*0=0.8$
Furthermore, the mode can be determined by solving for the extremum condition for each of the marginal distributions:
- $\frac{dp(x)}{dx}=0$
- $\frac{dp(y)}{dy}=0$
Finally, the medians can be found numerically using the following integrals:
- $\int^m_{-\infty} p(x)dx=\int^{+\infty}_m p(x) dx$
- $\int^m_{-\infty} p(y)dy=\int^{+\infty}_m p(y) dy$

3. Compute the mean and mode for the two-dimensional distribution.
The mean of a two-dimensional distribution can be found by creating a vector of the means found when calculating for the mean of the marginal distribution above:
$$\mu=
\begin{bmatrix}
4\\0.8
\end{bmatrix}$$
Furthermore, the mode is obtained by solving the extremum conditions:
- $\frac{\partial p(x)}{\partial x}=0$
- $\frac{\partial p(y)}{\partial y}=0$
---
## 6.5 Time-Series Model

$$\begin{aligned} \mathbf{x}_{t+1} &= \mathbf{A}\mathbf{x}_{t} + \mathbf{w}, \quad \mathbf{w} \sim \mathcal{N}(0, \mathbf{Q}) \\ \mathbf{y}_{t} &= \mathbf{C}\mathbf{x}_{t} + \mathbf{v}, \quad \mathbf{v} \sim \mathcal{N}(0, \mathbf{R}) \end{aligned}$$

where $\mathbf{w}, \mathbf{v}$ are i.i.d. Gaussian noise variables. Further, assume that $p(\mathbf{x}_{0}) = \mathcal{N}(\mu_{0}, \Sigma_{0})$.

1.  What is the form of $p(\mathbf{x}_{0}, \mathbf{x}_{1}, \dots, \mathbf{x}_{T})$? Justify your answer (you do not have to explicitly compute the joint distribution).

The time series model described is a Markov process because the current state depends only on the immediate state that comes after and no other states. 

The join distribution of the states $p(x_0, x_1, ... , x_T)$ can be expressed using the chain rule of probability, which allows us to decompose the join probability into a product of conditional probabilities:
$$p(x_0, x_1,...,x_T)=p(x_T|x_{T-1},...,x_0)\cdot p(x_{T-1}|x_{T-2},...,x_0)...p(x_1|x_2)\cdot p(x_0)$$
Because the state sequence is a Markov chain, the conditional probability of any state $x_t$ given all previous states simplifies to:
$$p(x_t|x_{t-1},x_{t-2},...,x_{0})=p(x_t|x_{t-1})\;\;\; \text{for }t\ge 1$$
Finally, when you apply the Markov property, the join distribution simplifies to:
$$
p(x_0,x_1,...,x_T)=p(x_0)\prod_{t=0}^{T-1}p(x_{t+1}|x_t)
$$
Therefore, the form $p(x_0,x_1,...,x_T)$ is a product of $T$ conditional Gaussian distributions and on initial Gaussian distributions.

2.  Assume that $p(\mathbf{x}_{t} \mid \mathbf{y}_{1}, \dots, \mathbf{y}_{t}) = \mathcal{N}(\mu_{t}, \Sigma_{t})$.

	1. Compute $p(\mathbf{x}_{t+1} \mid \mathbf{y}_{1}, \dots, \mathbf{y}_{t})$.
    
	2. Compute $p(\mathbf{x}_{t+1}, \mathbf{y}_{t+1} \mid \mathbf{y}_{1}, \dots, \mathbf{y}_{t})$.
    
	3. At time $t+1$, we observe the value $\mathbf{y}_{t+1} = \hat{\mathbf{y}}$. Compute the conditional distribution $p(\mathbf{x}_{t+1} \mid \mathbf{y}_{1}, \dots, \mathbf{y}_{t+1})$.
    