## David Jackson - 5298477

### Assignment:
While watching the videos keep a notebook ready (on paper or on the computer). 
- Take **notes (N:)** or **questions (Q:)** of one or two lines, prefixed by the time in the video. In particular, take a note when:
	- **(a)** something in the video provided you with new knowledge or insight or 
	- **(b)** something in the video is either not understandable or led to a new question.

---
# Lecture 1: Intro to Deep Learning (Mar 3, 2025)
1) **10:25 Q:** Artificial Intelligence is the most broad group of intelligent programming with the sub classes of machine learning and deep a further sub class of deep learning being shown; how do we classify problems to find out what type of algorithm is needed in order to obtain the end goal?

2) **16:39 Q:** While a feature is just a discrete detail hidden in the underlying data, is it better to try and manufacture features or try and find them naturally?

3) **16:39 Q:** What are some ways to obtain more natural features from your data?

4) **17:50 N:** I recall the idea of a feature pyramid from my robot vision class that layered the different level features allowing for a more robust and capable feature extraction method.

5) **19:09 - Q:** The presenter shows that Big Data, and Advances in both hardware and software are the reason Neural Networks are starting to show dominance in modern day software even though they date back to the 1950's.

6) **29:18 - N:** Dense layers are fully connected layers of perceptron's that learn the pattern of the features within the data.

7) **34:39 - N:** Fully Connected Dense Layers are much more computationally demanding than Convolutional layers.

8) **38:30 - Q:** How do you define custom loss functions for custom cases (ex: **object tracking by id**)?

9) **56:50 - Q:** How do these optimizers presented to us, such as ADAM, work? Obviously they are very technical optimizers but is there something within them that can be replicated throughout the models code base that could help greatly?

10) **1:03:12 - Q:** Is there a way to optimize Dropout in a way where it is only dropping out specific neurons with bad outputs or is the random aspect beneficial?

---
# Lecture 2: Deep Sequence Modeling (Mar 10, 2025)

1) **3:12 - Q:** Assuming we have a model that has runtime $\mathcal{X}$ and we are trying to graph $n$ sequences are we then just running the model over $n$ sequences with history being passed to each one causing the run time to be $\mathcal{X^{n}}$?

2) **12:30 - Q:** How do you define this function $f(x_t, h_{t-1})$ that is receiving the history from the prior neuron and the calculations from the current neuron?

3) **12:30 - Q:** If you receive a Loss for the entire sequence, how do you backpropagate over the sequences?

4) **17:39 - N:** The hidden state can be defined as the follows:
$$
\tag{Hidden State}
\begin{equation}
h_t=tanh(W_{hh}^Th_{t-1}+W_{xh}^Tx_t)
\end{equation}
$$
5) **20:12 - N:** The goal of an RNN is to minimize the loss over the entire sequence rather than just a single model.

6) **33:22 - Q:** How does One-hot embedding help with long term context?

7) **38:21 - N:** In regards to Question 3, the method you would use is BPTT (Backpropagate Through Time) however this has proven difficult to implement and unreliable so more research has shown that giving more control to the individual neuron has led to reliable results. The **LSTM** model (Long Short Term Memory) networks rely on a gated cell to track information throughout many time steps.

8) **52:31 - N:** Understanding Attention with searching, there are three sections that are important:
	1) Query - Search information
	2) Key - Value used to tag value
	3) Value - Return Value to user

9) **52:31 - N:** The Transformer architecture has 4 different parts:
	1) Encode **position** information
	2) Extract **query, key, value** for search
	3) Compute **attention weighting**
	4) Extract **features with high attention**

10) **57:40 - N:** Attention is the foundational building block of Transformers architecture.

---
# Lecture 3: Deep Computer Vision (Mar 17, 2025)

1) **10:03 - N:** The steps to object detection are fairly simple: 
	1) Define your features
	2) Find them
		- If found,  you have an object.

2) **12:00 - N:** Detecting features to classify is traditionally the step where machine learning breaks down and deep learning begins. This is because detecting features is a human search process which requires deep learning.

3) **19:00 - N:** A convolution is a kernel/filter with a set of weights that is updated when the CNN trains.

4) **19:00 - Q:** When the CNN trains how is backpropagation performed? Furthermore, how is it performed if it is within an RCNN?

5) **24:02 - N:** The convolution operator applies small filters over the input to extract **local** **features**, highlighting **patterns** such as **edges, textures, or shapes**.

6) **34:07 - N:** Recall from robot vision that convolutional layers typically use many filters (e.g., 32, 64, 128, 256, etc...) to capture diverse features.

7) **35:13** - N: ReLU the activation function just sets all negative to 0, since 0 is not a valid pixel value this is a good pre processing step.

8) **53:00 - N:** You need to be able to control how many objects are sent to the classifier or compute module of your network while not completely modulating your networks.

9) **56:00 - Q:** What is more computationally expensive and accurate, segmentation or detection and localization?

10) **58:09 - N:** I did not know that you could make a framework, especially one capable of autonomous Nav, without any human labelling or annotating for data. 

---
# Lecture 4: Deep Generative Modeling (Mar 24, 2025)

1) **3:35 - N:** The principle of generative modeling is: "Given a set along some random probability distribution, we want to train and build up a model that can learn the underlie probability distribution that describes and captures the space from which this data came."

2) **6:19 - N:** At the end of the last note I was thinking "wouldn't you always get the most probabilistic response" however, in the chance that your input is an edge case you will "leverage generative models to detect outliers".

3) **12:42 - N:** You are building a sort-of 'Translation Unit' between the generated data and the real data. The real data is used by the autoencoder to generated latent variables, the latent variables are lower-dimensional feature representation from unsupervised training. A generative version of the data is now created by using the latent variables to recreate the item. The more you compress the latent space, the more ground truth data you lose.

4) **17:00 - N:** **VAE's:** Instead of having a purely deterministic layer $Z$ we introduce stochasticity. Using the vectors $\text{means }(\mu)$ & $\text{Standard Deviation }(\sigma)$ we can get a distribution over all the latent variables in our latent space.

5) **22:00 - N:** Common choice of prior is a normal gaussian.

6) **22:45 - N:** KL-divergence is a way to compute and quantify the distance between two different probability distributions.

7) **29:30 - N:** This is one of the only Deep learning networks where you are able to inspect the features being evaluated and picked up by your network (VAE).

8) **33:30 - N:** The principal of GAN is "How closely can we generate the data that our model is trained on?"

9) **36:55 - N:** The GAN network has 2 aspects, the discriminator and the Generator. The Generator is trying to generate real data that tricks the Discriminator mean while the Discriminator is the gate keeper not letter the false data go by. The idea is to optimize both networks in parallel as data is fed through.

10) **41:24 - N:** The domain transformation was pretty cool and I didn't know that could happen.


---

# Resources:
https://introtodeeplearning.com/

#### Lectures 1-4
- **Lecture 1:** Intro to Deep Learning (Mar 3, 2025)
	 - https://www.youtube.com/watch?v=alfdI7S6wCY
- **Lecture 2:** Deep Sequence Modeling (Mar 10, 2025)
	- https://www.youtube.com/watch?v=GvezxUdLrEk
- **Lecture 3:** Deep Computer Vision (Mar 17, 2025)
	- https://www.youtube.com/watch?v=oGpzWAlP5p0
- **Lecture 4:** Deep Generative Modeling (Mar 24, 2025)
	- https://www.youtube.com/watch?v=SdTZAMDKrNY