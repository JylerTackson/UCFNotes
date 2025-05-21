### What is a Perceptron?
Perceptron's are a the most basic **supervised** machine learning algorithm used for **binary classification**. Perceptron's are the inspiration behind neural networks. A perceptron can be thought of as a single neuron (that can only be used on linear data) and when you combine these neurons you create a network resulting in 'neural nets'. Perceptron's create a **decision boundary** that separates the **two** classes.

### How does a Perceptron work?
###### Slides:
1) Set the initial conditions:
	   With the first iteration, initialize all weight vectors to be 0 (meaning the model knows nothing to start with) 
2) Make a Prediction:
		Using a linear equation: 
		$$h(x) = w \cdot x + w_0$$
3) Evaluate Prediction using label:
	The weights of the perceptron are only updated if the prediction is **incorrect**:
		- Mistake on **positive**, update: $\mathbf{w_{t+1}\leftarrow w_t + x}$
		- Mistake on **negative**, update: $\mathbf{w_{t+1}\leftarrow w_t - x}$
###### Wikipedia:
1) Initialize the weights. (The weights may be Initialize to 0 or a small random value)
2) For each example $j$ in our training set $D$, perform the following steps over the input: $\mathbf{x_j}$ and the output: $\mathbf{d_j}$ :
	1) Calculate the actual output:
		$$y_j(t)=f[w(t)\cdot x_j]$$
	$$y_j(t)=f[w_0 (t)x_{j,0} +w_1(t)x_{j,1} + w_2(t)x_{j,2} \;+ ... +\; w_n (t)x_{j,n}]$$
	2) Update the weights:
	$$
w_i(t+1)=w_i(t)+r\;\cdot\;(d_j-y_j(t))x_{j,i} \;\; \text{for all features }\;\; 0 \leq i \leq n, \;\; \text{Where } r \text{ is the learning rate}
$$
3) For **offline learning** the second step my be repeated until the iteration error is less than a user-specified threshold $(\gamma)$.

### How does a perceptron learn?
Perceptron's are an **online learning model** meaning that it can learn in real time given real time data. The model is presented with a new data point (input features), using this input it will make a prediction using the previous data given to it. Once the prediction is made the model will observe the prediction against the data's true label (loss function). If the model was **wrong** the model will update the weights, if the model was correct, the weights will remain the same.

###### Mistake Bound Model:
The goal of this model is to minimize the number of mistakes the model makes over time as fast as possible. The model doesn't assume the data follows a specific pattern of data distribution **instead**, the **number of mistakes** the perceptron makes is **bounded** using a threshold number $(\Gamma)$. For Linearly Separable data, the number of mistakes the model makes can always be bounded using the distribution to predict the amount of mistakes that will occur while creating the decision boundary. If the distribution is large (distance between classes) than the number of mistakes will be less, vice versa for a smaller distribution. From this we can say that the number of mistakes is inversely proportional to the margin $(\gamma)$ and larger spread data points (larger $\mathbf{R}$) will lead to more mistakes.

The mistake Bound is a mathematical guarantee of how many mistakes the model will make but when applying the threshold number you must do it dynamically based on the data you have. If the data has a **margin of** $\mathbf{\gamma}$ and your data points like inside a **radius** $\mathbf{R}$ your mistake bound threshold can be calculated as:
$$\Gamma=\left(\dfrac{R}\gamma\right)^2
$$
 
###### Geometric Margin (Loss Function):
The Geometric margin is a measure of how far a point is from the decision boundary. A **larger positive margin** indicates a more confident and accurate classification while a smaller or negative margin indicates a less confident or incorrect classification.

###### Perceptron's in a batch setting (Offline Learning):
In this example, we have a dataset $(\mathbf{S})$ and we want to use a perceptron to find a linear separator to classify these data points within $\mathbf{S}$. To do this we will repeatedly feed the dataset to the perceptron until we find a linear separator that is able to classify ALL data points within $\mathbf{S}$. We can approximate the amount of mistakes the model will make using:
$$
\Gamma=\left(\dfrac{R}\gamma\right)^2 + 1
$$
