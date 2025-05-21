#### Problem 1:
Given the following language $L$, construct a **DFA** that accepts all members.
$$
\begin{equation}\tag{P.1}
L=\{w\in\{a,b\}^*:w \text{ has the suffix }aba\}
\end{equation}
$$
**NOTE:** $w\in\{a,b\}^*$ means that the string $(w)$ can contain all possible combinations $(*)$ of the alphabet as long as it has the suffix of $aba$. 
**NOTE:** Since we are dealing with the **suffix** of the string $(w)$, instead of **prefix**, we are feeding in the letters of the string into system reverse instead of forward.

To construct a **DFA** given the language above we can use the formal definition of a DFA:
$$
\begin{equation}\tag{DFA}
M_1=(Q,\Sigma,\delta,q_o,F)
\end{equation}
$$
Where:
- $Q$ is the set of states:
	- The states we have are:
		- $q_0 = \text{start state}$
		- $q_1 = \text{seen 'a'}$
		- $q_2 = \text{seen 'ab'}$
		- $q_3 = \text{seen 'aba'}$
		- $q_4 = \text{dead state}$
			- $\therefore Q\Rightarrow\{q_0, q_1, q_2, q_3, q_4\}$
- $\Sigma$ is the alphabet set:
	- There are only 2 symbols in the alphabet:
		- $\Sigma = \{a,b\}$
- $\delta$ is the transition function between states:

|       | **a** | **b** |
| ----- | ----- | ----- |
| $q_0$ | $q_1$ | $q_3$ |
| $q_1$ | $q_4$ | $q_2$ |
| $q_2$ | $q_3$ | $q_4$ |
| $q_3$ | $q_3$ | $q_3$ |
| $q_4$ | $q_4$ | $q_4$ |

- $q_o$ is the start state:
	- The start state is $q_0$
		- This is where the system begins.
- $F$ is the final state:
	- The final state is $q_3$
		- $q_3$ is the state where string $(w)$ has been confirmed to have the suffix of $'aba'$
$$
\begin{equation}\tag{A.1}
M_1=\{\{q_0,q_1,q_2,q_3,q_4\},\{a,b\},\delta,q_0,q_3\}
\end{equation}
$$
---
#### Problem 2:
Given the following language $L$, construct a **DFA** that accepts all members.
$$
\begin{equation}\tag{P.2}
L=\{a^nb:n\geq0\}
\end{equation}
$$
To construct the DFA we can use the formal definition:
- $Q$ is the states:
	- $q_0 \Rightarrow \text{start state}$
	- $q_1 \Rightarrow \text{seen 'a'}$
	- $q_2 \Rightarrow \text{seen '}a^n\text{b'}$
	- $q_3 \Rightarrow \text{Dead State}$
- $\Sigma$ is the alphabet:
	- $\Sigma = \{a,b\}$
- $\delta$ is the transition functions:

|       | $a$   | $b$   |
| ----- | ----- | ----- |
| $q_0$ | $q_1$ | $q_3$ |
| $q_1$ | $q_1$ | $q_2$ |
| $q_2$ | $q_3$ | $q_3$ |
| $q_3$ | $q_3$ | $q_3$ |
- Start state is $q_0$
- $F$ is the final state:
	- Final state is $q_2$
		- At this state, if there is another input read then the machine will immediately send the input to the dead state. 
$$
\begin{equation}\tag{A.2}
M_2=\{\{q_0,q_1,q_2,q_3\},\{a,b\},\delta,q_0,q_2\}
\end{equation}
$$
---
#### Problem 3:
Given the following language $L$, construct a **DFA** that accepts all members.
$$
\begin{equation}\tag{P.3}
L=\{w\in\{a,b\}^*: w \text{ has the prefix } aa\}
\end{equation}
$$
**NOTE:** we are feeding the string into the system forward, we are dealing with the **prefix**.

To construct the DFA we can use the formal definition:
- $Q$ is the states:
	- $q_0 \Rightarrow \text{start state}$
	- $q_1 \Rightarrow \text{seen 'a'}$
	- $q_2 \Rightarrow \text{seen 'aa'}$
	- $q_3 \Rightarrow \text{dead state}$
		- $\therefore Q=\{q_0,q_1,q_2,q_3\}$
- $\Sigma$ is the alphabet:
	- $\Sigma=\{a,b\}$
- $\delta$ is the transition function between the states.

|       | $a$   | $b$   |
| ----- | ----- | ----- |
| $q_0$ | $q_1$ | $q_3$ |
| $q_1$ | $q_2$ | $q_3$ |
| $q_2$ | $q_2$ | $q_2$ |
| $q_3$ | $q_3$ | $q_3$ |
- $q_0$ is the starting state of the system
- $F$ is the final state of the system
	- $q_2$ at this state the system has confirmed that the prefix $'aa'$ is in string $w$ 
$$
\begin{equation}\tag{A.3}
M_3=\{\{q_0,q_1,q_2,q_3\}, \{a,b\}, \delta, q_0, q_2\}
\end{equation}
$$
---
#### Problem 4:
Given the following language $L$, construct a **DFA** that accepts all members.
$$
\begin{equation}\tag{P.4}
L=\{awa:w\in\{a,b\}^*\}
\end{equation}
$$
**NOTE:** we are dealing with **both** a **prefix & suffix.** We must loop through the entire string $(w)$ while only confirming the string is valid if the first and last string are $'a'$.

Construct the DFA:
- States:
	- $q_0 \Rightarrow \text{input state}$
	- $q_1 \Rightarrow \text{seen 'a'}$
	- $q_2 \Rightarrow \text{seen 'aa'}$
	- $q_3 \Rightarrow \text{dead state}$
		- $Q=\{q_0,q_1,q_2,q_3\}$
- Alphabet:
	- $\Sigma={a,b}$
- Transition Functions:

|       | $a$   | $b$   |
| ----- | ----- | ----- |
| $q_0$ | $q_1$ | $q_3$ |
| $q_1$ | $q_2$ | $q_3$ |
| $q_2$ | $q_2$ | $q_3$ |
| $q_3$ | $q_3$ | $q_3$ |

- Start state:
	- $q_0$ is where the initial input is fed
- Final state:
	- $q_2$ is where the final state is confirmed to have a prefix and suffix of $'a'$.
$$
\begin{equation}\tag{A.4}
M_4=\{\{q_0,q_1,q_2,q_3\},\{a,b\},\delta,q_0,q_2\}
\end{equation}
$$
---
#### Problem 5:
Given $\Sigma=\{0,1\}$, describe the language recognized by the following DFA.
![[2025-05-17-104625_489x167_scrot.png]]

---
#### Problem 6:
Given $\Sigma=\{a,b\}$, construct a DFA that accepts all members of the following language $L$.
$$
\begin{equation}\tag{P.6}
L=\{w:|w|\;mod3\neq0\}
\end{equation}
$$
**NOTE:** We are not dealing with prefix or suffix in this problem; the language is defining a string $(w)$ and we are using the **string length** $|w|$ to finalize the string.

To construct the DFA, I will use the 5-tuple definition of a DFA:
- $Q$ for states:
	- $q_0 \Rightarrow \text{start state}$
	- $q_1 \Rightarrow \text{|w| mod3} \neq 0$
	- $q_2 \Rightarrow \text{|w| mod3} = 0$
	- $q_3 \Rightarrow \text{dead state}$
- $\Sigma$ for alphabet:
	- $\Sigma = \{a,b\}$
- $\delta$ for transition functions:

|       | $w\mathbf{mod}3=0$ | $w\mathbf{mod}3\neq0$ |
| ----- | ------------------ | --------------------- |
| $q_0$ |                    |                       |
| $q_1$ |                    |                       |
| $q_2$ |                    |                       |
| $q_3$ |                    |                       |
- $q_0$ is the start state
- $F$ is the final state
---
#### Problem 7:
Given the following language $L$, construct a DFA that accepts all members.
$$
\begin{equation}\tag{P.7}
L=\{ba^n:n\geq1,n\neq4\}
\end{equation}
$$


---
#### Problem 8:
Given $\Sigma=\{a,b\}$, construct a DFA that accepts all strings with at least one $b$ and **exactly** two $a's$.

---
#### Problem 9:
Given $\Sigma=\{a,b\}$, construct a DFA that accepts all strings with an **even number** of $a's$ and an **odd number** of $b's$.