Principle Component Analysis transforms data into new features known as your principal components. It does this by calculating eigenvectors and eigenvalues from the covariance matrix. PCA selects the top components with the highest eigenvalues and projects the data onto them simplifying the dataset.

#### Steps:
1) Standardize the dataset by making each feature have:
	- A mean of 0
	- A standard deviation of 1
$$
Z=\frac{X-\mu}{\sigma}
$$
2) Calculate the Covariance Matrix
	- PCA calculates the Covariance matrix to see how features relate to one another.
$$
\mathbb{V}_X[x,x]=\;
\begin{bmatrix}
\operatorname{Cov}[x_1, x_1] & \operatorname{Cov}[x_1, x_2] & \cdots & \operatorname{Cov}[x_1, x_D] \\
\operatorname{Cov}[x_2, x_1] & \operatorname{Cov}[x_2, x_2] & \cdots & \operatorname{Cov}[x_2, x_D] \\
\vdots & \vdots & \ddots & \vdots \\
\operatorname{Cov}[x_D, x_1] & \cdots & \cdots & \operatorname{Cov}[x_D, x_D]
\end{bmatrix}
$$
3) Find the Principal Components
	- PCA identifies new axes where the data spreads out the most
		- **1st Principal Components (PC1):** The direction of maximum variance
		- **2nd Principal Components (PC2):** The next best direction, perpendicular to PC1.

4) Pick the top Directions & Transform Data
	- After calculating eigenvalues and vectors select the top k components that capture $\sim 95\%$ of the variance and transform the original dataset by projecting it onto these components.