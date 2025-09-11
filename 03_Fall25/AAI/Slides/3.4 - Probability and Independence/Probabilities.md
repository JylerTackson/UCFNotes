Topics:
- [[#Random variable|Random Variables]]
- [[#Joint Distribution|Joint Distributions]]
- [[#Marginal Distributions|Marginal Distribution]]
- [[#Conditional Distributions|Conditional distributions]]
- Rules:
	- [[#The Product Rule|Product Rule]]
	- [[#The Chain Rule|Chain Rule]]
	- [[#The Bayes' Rules| Bayes` Rule]]

---
##### Uncertainty
**Observed Variables:**
- These are observations that the agent makes about the world, whether they are incomplete or noisy. They do not directly correspond to the state of the world.
	- **EX:** Medical Test
- **Probabilistic model**: the agent knows something about how the known variables relate to the unknown
**Unobserved Variables:**
- The agent needs to reason about the state of the world to infer these variables
	- **EX:** Medical Diagnosis
- **Probabilistic reasoning:** framework to manage beliefs and knowledge

##### Random variable
An aspect of the world about which we might have uncertainty
- Always denoted with capital letters $(\mathcal{R},\mathcal{T},\mathcal{S})$
They have their own domains can can be either **discrete** or **continuous**
- $\mathcal{R}\in\{true, false\}$
- $\mathcal{T}\in[0,\infty)$

#### Probability distributions
Associate a probability with each value in the domain.

A **probability** is a single number: 
- $P(false)=0\to0.5 \text{ \& } P(true)=0.5\to 1$
A distribution is a table of probabilities of values
$$
\begin{matrix}
&P(T)=\\
(T)&&(P(T))\\
hot&\Rightarrow&0\to0.499...99\\
cold&\Rightarrow&0.5\to1
\end{matrix}
$$
Must have
- $\forall(x)P(X=x)\geq 0 \text{ and } \sum_x P(X=x)=1$
	- Axioms of a probability mass function for a discrete random variable $\mathcal{X}$
		- $\forall(x)P(X=x)\geq 0$ The probability cannot be negative
		- $\sum_x P(X=x)=1$ The probability of all the outcomes summed must be equal to 1


##### Joint Distribution
A joint distribution over a set of random variables $\{\mathcal{X}_1, \mathcal{X}_2,..., \mathcal{X}_n\}$ specifies a real number for each assignment (outcome).
$$P(\mathcal{X}_1=x_1, \mathcal{X}_2=x_2, ... , \mathcal{X}_n=x_n)$$ or can be simplified to $P(x_1, x_2, ..., x_n)$
$$
\begin{matrix}
&P(T,W)=\\
(T)&(W)&(P)\\
hot&sun&0.8\\
cold&sun&0.3
\end{matrix}
$$
##### Probabilistic model
A model is a joint distribution over a set of random variables
- A set of random variables with domains
- Assignments are called outcomes
	- Known Variables
- Join Distribution say which outcomes are more likely
- Normalized: Sum to 1

##### Events
An event is a set $E$ of outcomes
- Events we care about are typically partial assignments
- If we have a joint distribution, we can calculate the probability of **any** event:

##### Marginal Distributions
Sub-tables that eliminate variables by using marginalization to combine collapsed rows by adding their probabilities. We can turn our **joint** **distribution** $P_J$ into a **marginal distribution** $P_M$ by removing the $T$ column and summing the $P$ column for the $W$ variables.
$$
\begin{matrix}
P_{J}&&&&P_{M}\\
\left[\begin{matrix}
T & W & P \\
hot & sun & 0.4 \\
hot & rain & 0.1 \\
cold & sun & 0.2 \\
cold & rain & 0.3 
\end{matrix}\right]
&&
\Rightarrow
&&
\left[\begin{matrix}
W & P \\
sun & 0.6 \\
rain & 0.4
\end{matrix}\right]
\end{matrix}
$$

##### Conditional probabilities
**Definition:**
$$P(a|b)=\frac{P(a,b)}{P(b)}$$
Example:
$$P(sun|cold)=\frac{P(sun,cold)}{P(cold)}=\frac{0.2}{0.5}=0.4$$
##### Conditional Distributions
$$\begin{matrix}

\begin{matrix}
p(w|t=hot)\\
\left[
\begin{matrix}
W&P\\
sun&0.8\\
rain&0.2
\end{matrix}
\right]
\end{matrix}
&&

&&
\begin{matrix}
p(w|t=cold)\\
\left[
\begin{matrix}
W&P\\
sun&0.4\\
rain&0.6
\end{matrix}
\right]
\end{matrix}
\end{matrix}$$
#### Normalization
Procedure
- Compute $\mathcal{Z}=$ sum over all the entries
- Divide every entry by $\mathcal{Z}$ (also called **normalization constant** or **partition function**)

Premonition
- Normalization is simple as a procedure
- ...but in more complex situations, it is a huge problem, because I need to sum over all possible alternatives... 

##### Normalization trick
To calculate the conditional distribution table for a certain evidence just start with the join table.
- Two Steps:
  1) **Select** the join probabilities matching the evidence
  2) **Normalize** the selection (make it sum to 1.0)
	- This works because the sum of selection is the $P(evidence)$
	$$
	\begin{equation}\tag{Sum of Selection}
	P(x_1|x_2)=\frac{P(x_1,x_2)}{P(x_2)}=\frac{P(x_1,x_2)}{\sum_{x_1} P(x_1,x_2)}
	\end{equation}$$

##### Probabilistic inference
Generally we are interested to compute a certain probabilities based upon other probabilities that we may know. Most of the time we are interested in the $\mathcal{P_{J}}$ where:
- $\mathcal{P_{J}}(x|e_1,e_2,...,e_n)$
- This is called the **belief** of the agent given the **evidence**.

##### Inference by Enumeration
General case:
- Evidence Variables: $E_1,...,E_K=e_1,...,e_k$
- Query$*$ Variables: $Q$
- Hidden variables: $H_1, ..., H_r$

What we want:
- $P(Q|e_1,...,e_k)$

How to get there:
1) Select the entries consistent with the evidence
2) Sum out H to get joint of Query and evidence
3) Normalize
![[Pasted image 20250829221035.png]]

#### Rules

##### The Product Rule
It is not really a "rule", just turning around the definition of the conditional
$$\tag{Product Rule}P(y)P(x|y)=P(x,y)$$

###### The Chain Rule
Extending the product rule to multiple conditionals
$$\tag{The Chain Rule}
\begin{matrix}
P(x_1,x_2,x_3)=P(x_1)P(x_2|x_1)P(x_3|x_1,x_2)
\\
P(x_1,x_2,...x_n)=\prod_iP(x_i|x_1,...,x_i-1)
\end{matrix}
$$

#### The Bayes' Rules
1) Allows us to calculate $P(x|y)$ from $P(y|x)$
2) There are many scenarios where one conditional is difficult, but the reverse is not
	- $P(covid|high\_fever)$ how do we even start to think about this?
	- $P(hight\_ fever|covid)$ - easy peasy, about 0.9


##### Definition
There are a few things to understand about the Bayes rules:
1) Order of the variables does not matter
	- $P(x,y)=P(y=x)$
2) Product Rule and Chain Rule can be written for any of these orders:
$$P(x,y)=P(x|y)P(y)=P(y|x)P(x)$$
	- Dividing, we get **Bayes' rule**
$$\tag{Bayes' Rule}P(x|y)=\frac{P(y|x)}{P(y)}P(x)$$

##### Inference
Given the example:
- $m$: meningitis
- $s$: stiff neck
$$
\begin{matrix}
P(+m=0.0001)\\
P(+s|+m)=0.8\\
P(+s|-m)=0.01
\end{matrix}
$$
We want to calculate $P(+m|+s)$, to do that we are going to apply bayes' rule:
$$P(+m|+s)=\frac{P(+s|+m)P(+m)}{P(+s)}$$
We dont have $P(+s)!$ But we get it by marginalization
$$P(+s)=P(+s,+m)+P(+s,-m)$$
And get the joints from the conditionals using the product rule
$$
\begin{matrix}
P(+s,+m)=P(+s|+m)+P(+m)
\\
P(+s,m)=P(+s|-m)P(-m)
\end{matrix}
$$
Also due to probabilities summing to 1.0
$$P(-m)=1.0-P(+m)$$
$$P(+m|+s)=\frac{0.8\times0.0001}{0.8\times0.0001+0.01\times0.9999}$$
Notes:
- It is about 0.00795, approximately 0.8%
- So, just because you have a stiff neck, the likelihood of meningitis is still low due to the overall occurrences of meningitis being low.
- BIG PROBLEM for many diagnosis systems because a test a symptom appeas for a for a certain disease might still not be a good predictor.