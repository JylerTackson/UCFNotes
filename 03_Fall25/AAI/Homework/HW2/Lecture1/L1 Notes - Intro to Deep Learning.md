## Why Deep Learning? (15:30)


## Applying Neural Networks (35:30)
As learned in previous classes, you cannot just throw a neural net in use without training it, you train a neural net by testing its prediction with actual values using loss functions.

**Loss functions:**

Quantifying Loss
- The loss of our network measures the cost incurred from incorrect predictions.
Empirical Loss
- The empirical loss measures the total loss over our **entire dataset**.

Binary Output
- SoftMax Cross Entropy
Regression Output
- Mean Squared Error

# Training Neural Networks (41:06)
How do we train:
We are aiming to optimize our model by minimizing the loss by adjusting the weights of our model.

Gradient Descent:
1) Initialize weights randomly
2) Loop until convergence:
	- Compute gradient $\frac{\partial J(W)}{\partial (W)}$
	- Update weights, $W\leftarrow W-\alpha(\frac{\partial J(W)}{\partial (W)})$
3) Return Weights

# Neural Networks in Practice: 
Go's over several of the key important parts of Neural Nets:

## Optimization (48:30)

How to set the learning rate to accurate backpropagate; your learning rate should be set dynamically depending on several factors such as:
- How large the gradient is
- How fast learning is happening
- size of particular weights
- etc...

Current Model Gradient Descent Algorithms:
- SGD
- Adam$^\star$
- Adadelta
- Adagrad
- RMSProp

## Mini Batches (52:30)
More accurate estimation of gradient by using small "batches" of data to calculate the gradient rather than calculating over the entire dataset. Allows for smoother convergences and larger learning rates for faster training.

## Overfitting & Underfitting (56:30)
We don't care too much how data works on training data, it is a proxy on how the data should perform on unseen data that has similar features to the training data.

**Underfitting:**
- Model does not have capacity to full learn the data and performs poorly on training data and unseen data.
**Overfitting:**
- Data is Too complex, has extra unneeded parameters, and the model is not able to generalize for unseen data.

Regularization Techniques to avoid above data issues:
- **Dropout:**
	- Randomly set some activations of neurons to 0
- **Early Stopping** 
	- Stops training early before the model is able to overfit.