Sequence Modeling can be thought of the process of taking the sequences presented as data and making an educated prediction based on  the provided sequences on what will happen next.

Sequence Modeling can be seen all around us such as:
- Sounds
- Words
- Characters
- Medical Signals
- Stock Prices
- Etc...

Applications:
- Many to One
	- Classification of something with many features
- One to Many
	- A single feature being broken up (such as generating a sentence to describe an image)
- Many to Many
	- Many features to Many features (such as machine translation)

# Recurrent Neural Nets
The way we link Neural Nets to sequential data is through a recurrent neural network. Our goal is to pass the information from each neurons internal state, from each time step, to the next time step we can introduce a variable that will be passed on across time.
![[Pasted image 20250820200023.png]]


Recurrence Relation is applied at every time step to process a sequence
$h_t=f_w(x+t, h_{t-1})$

There are several steps to how a RNN updates its state:
$W_{}$


Output Vector:
- $\overline{y_t}=W_{hy}^Th_t$
Update Hidden State:
- $h_t=tanh(W_{hh}^Th_{t-1}+W_{xh}^Tx_t)$
Input Vector:
- $x_t$
