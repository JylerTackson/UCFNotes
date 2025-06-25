# Homework 2 - 60pts
## David Jackson
## 5298477
## Discrete 2 - COT4210
## Steinberg

## 1. NFA Conversion
(15 points) Convert the following NFA to its equivalent DFA using the procedure learned in class that produces all possible states. You may assume that Σ = {a, b}. From your resulting picture, which states are unreachable based on the possibilities from the DFA?![[Pasted image 20250607234010.png]]

To begin, first you must identify you set of states within your NFA:
- $Q_N=\{0,1,2\}$
The state of sets within your DFA will be the power set of your states in your NFA:
- $Q_D=P(Q_D)=\{0,1,2,01,02,12,012,\emptyset\}$
	- We do not include repeats
Now that we have our set of states, we define our transition functions:
- $\delta(q_0,a)=\{q_1,q_2\}=q_{12}$
- $\delta(q_0,b)= \{q_1, q_2\}=q_{12}$
- $\delta(q_1,a)=\{q_0,q_2\}=q_{02}$
- $\delta(q_1,b)=\{q_1, q_2\}=q_{12}$
- $\delta(q_2,a)=\{q_\emptyset\}=q_\emptyset$
- $\delta(q_2,b)=\{q_1,q_2\}=q_{12}$

- $\delta(\{q_0,q_1\},a)=\delta(q_0,a)\cup\delta(q_1,a)=\{q_1,q_2\}\cup\{q_0,q_2\}=\{q_0,q_1,q_2\}=q_{012}$
- $\delta(\{q_0,q_1\},b)=\delta(q_0,b)\cup\delta(q_1,b)=\{q_1,q_2\}\cup\{q_1,q_2\}=\{q_1,q_2\}=q_{12}$
- $\delta(\{q_0,q_2\},a)=\delta(q_0,a)\cup\delta(q_2,a)=\{q_1,q_2\}\cup\{q_\emptyset\}=\{q_1,q_2\}=q_{12}$
- $\delta(\{q_0,q_2\},b)=\delta(q_0,b)\cup\delta(q_2,b)=\{q_1,q_2\}\cup\{q_1,q_2\}=\{q_1,q_2\}=q_{12}$
- $\delta(\{q_1,q_2\},a)=\delta(q_1,a)\cup\delta(q_2,a)=\{q_0,q_2\}\cup\{q_\emptyset\}=\{q_\emptyset\}=q_{02}$
- $\delta(\{q_1,q_2\},b)=\delta(q_1,b)\cup\delta(q_2,b)=\{q_1,q_2\}\cup\{q_1,q_2\}=\{q_1,q_2\}=q_{12}$

- $\delta(\{q_0,q_1,q_2\},a)=\{q_0,q_1,q_2\}=q_{012}$
- $\delta(\{q_0,q_1,q_2\},b)=\{q_1,q_2\}=q_{12}$
Finally we define our start and accept states:
- Since $q_0$ is the start state in the NFA it will remain in the DFA
- Since $q_1$ is the accept state in the NFA, any state with 1 in it will become an accept state:
	- $F_D=\{q_1,q_01,q_12,q_012\}$
Our DFA is:
![[Pasted image 20250608003057.png]]
However to clean it up you can remove the dead-states which our states that are never reached.
The only states that can ever be reached are:
- $q_0, q_{02}, q_{12}$
Resulting in:
![[Pasted image 20250608003247.png]]

---
## 2. RegEx
15 points) In the C programming language, a value can be designated as a character type through a declaration statement where the prefix starts with char and ends with the suffix ;. Between the prefix and suffix is the name of the variable. Let C be the language of valid character declaration statements. A member of C must start with char and end with ;. The member must have at least 2 characters in its variable name and cannot contain the ; character. For example, the statement `char nums;` is valid since nums has 4 characters, but `char x;` is not valid since x is only one character. For simplicity, assume that the alphabet for C is $\Sigma = \{a, b, c, d, e, h, i, r, ; \}$. Give a regular expression that generates C. You cannot use the set difference when creating your regular expression. Please write out the possible set of symbols that can be generated.

Restrictions:
- Must start with the prefix: `char`
- Must contain **at least** 2 characters within $\Sigma$ (excluding $;$)
- Must end with the suffix: `;`
- Can NOT use set difference.

$$\begin{equation}\tag{A.2}
r_C=\{char\circ\{a | b | c | d | e | h | i | r\}^+\circ\{a | b | c | d | e | h | i | r\}^+\circ\mathbf{;}\}
\end{equation}$$
- This expression satisfies the requirements
	1) Concatenates the prefix `char`
	2) Uses every valid symbol from alphabet
		- Excludes `;`
		- Includes all symbols by using the `|` OR operation
	3) Specifies positive closure which excludes the null string.
	4) Finally Concatenates the suffix `;`
---
## 3. Proof by Construction
(15 points) Let A and B be regular languages. We define the following operation PSHUFFLE. 

$$\begin{equation}
PSHUFFLE(A,B) = \{w | w = a^1b^1...a^kb^k,\text{ where }a^1...a^k ∈ A\text{ and }b^1...b^k ∈ B,\text{ each }a^i, b^i ∈ Σ\}.
\end{equation}$$

Show that the class of regular languages is closed under **PSHUFFLE**. You will need to write out a proof. Hint, use a proof by construction technique.

**PSHUFFLE** zips two strings of equal length together, taking one symbol from a word in _A_, then one from a word in _B_, and so on.
To recognize such words we only need to:
1) Remember whose turn it is
2) Run the usual DFA's for A & B on the symbols that belong to them.
Because DFAs are closed under direct product, adding a single parity will still yields a DFA.

Since both A and B are both regular languages they both have a DFA that represent them therefore we can say:
$$\begin{equation}
D_A = \{Q_A,\Sigma_A,\delta_A,q_A,F_A\}
\end{equation}$$
$$\begin{equation}
D_B = \{Q_B,\Sigma_B,\delta_B,q_B,F_B\}
\end{equation}$$
To show that **PSHUFFLE** is a regular language we can define a new DFA s.t.:
$$\begin{equation}
M_{PSHUFFLE}=\{Q_P,\Sigma_P,\delta_P,q_P,F_P\}
\end{equation}$$
We will need a method of determining which $\delta_{A,B}$ to use and for that we will use:
$$\begin{equation}\tag{Turn Bit}
t=\{0,1\}
\end{equation}$$
The turn bit will determine which transition function to use. For example:
$$\begin{equation}\tag{t=0}
\text{If t=0 use }\delta_A
\end{equation}$$
$$\begin{equation}\tag{t=1}
\text{If t=1 use }\delta_B
\end{equation}$$
This is the method that will determine which languages "turn" it is aka parity.

Finally with this in mind, we know that:
$$\begin{equation}
Q_M=Q_A\times Q_B \times \{0,1\}
\end{equation}$$
$$\begin{equation}
|Q_M|=|Q_A|\times |Q_B| \times |\{0,1\}|< \infty
\end{equation}$$
$\therefore$ **PSHUFFLE** is a regular language.
$$QED$$

---
## 4. DFA $\rightarrow$ GFNA
(15 points) Convert the DFA into a Regular Expression using the GNFA procedure learned in class. Make sure to show your work/reasoning when performing the repair procedure in order to receive potential credit. Assume that $\Sigma = \{a, b\}$. Please do not worry about simplifying your regular expression in the final answer.
![[Pasted image 20250608135926.png]]
The first step I will do is insert the **Start & Accept states** within this DFA so I can begin the **Rip & Repair** procedures:
![[Pasted image 20250608142028.png]]
To transfer the given DFA to a GFNA we will use the **Remove & Repair** procedure. As shown in class we will make a table:

Using the standard "rip-and-repair" update rule:
$$\begin{equation}\tag{R.A.R}
R^\prime_{a,b}=R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}
\end{equation}$$
We can define the new transition from $a \rightarrow b$ while excluding the rip state $(r)$.
1) Rip $q_0$

| a     | r     | b     | $R_{a,r}$ | $R_{r,r}$   | $R_{r,b}$ | $R_{a,b}$   | $R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}$      | $R^\prime_{a,b}$ |
| ----- | ----- | ----- | --------- | ----------- | --------- | ----------- | -------------------------------------------- | ---------------- |
| $q_s$ | $q_0$ | $q_1$ | $\lambda$ | $\emptyset$ | $\{a,b\}$ | $\emptyset$ | $\emptyset \cup \lambda(\emptyset)^*\{a,b\}$ | $\lambda\{a,b\}$ |

![[Pasted image 20250608144945.png]]
2) Rip $q_2$

| a     | r     | b     | $R_{a,r}$ | $R_{r,r}$   | $R_{r,b}$ | $R_{a,b}$   | $R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}$ | $R^\prime_{a,b}$ |
| ----- | ----- | ----- | --------- | ----------- | --------- | ----------- | --------------------------------------- | ---------------- |
| $q_1$ | $q_2$ | $q_3$ | $a$       | $\emptyset$ | $b$       | $\emptyset$ | $\emptyset \cup a(\emptyset)^*b$        | $ab$             |
| $q_1$ | $q_2$ | $q_F$ | $a$       | $\emptyset$ | $\lambda$ | $\emptyset$ | $\emptyset \cup a(\emptyset)^*\lambda$  | $a\lambda$       |
| $q_1$ | $q_2$ | $q_4$ | $a$       | $\emptyset$ | $\{a,b\}$ | $\emptyset$ | $\emptyset \cup a(\emptyset)^*\{a,b\}$  | $a\{a,b\}$       |
![[Pasted image 20250608173241.png]]
3) Rip $q_3$

| a     | r     | b     | $R_{a,r}$ | $R_{r,r}$   | $R_{r,b}$ | $R_{a,b}$        | $R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}$      | $R^\prime_{a,b}$                |
| ----- | ----- | ----- | --------- | ----------- | --------- | ---------------- | -------------------------------------------- | ------------------------------- |
| $q_1$ | $q_3$ | $q_4$ | $ab$      | $\emptyset$ | $\{a,b\}$ | $b\cup a\{a,b\}$ | $b\cup a\{a,b\} \cup ab(\emptyset)^*\{a,b\}$ | $b\cup a\{a,b\} \cup ab\{a,b\}$ |
| $q_1$ | $q_3$ | $q_1$ | $ab$      | $\emptyset$ | $a$       | $\emptyset$      | $\emptyset \cup ab(\emptyset)^*a$            | $aba$                           |

![[Pasted image 20250608234658.png]]
4) Rip $q_1$

| a     | r     | b     | $R_{a,r}$         | $R_{r,r}$ | $R_{r,b}$                       | $R_{a,b}$   | $R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}$                               | $R^\prime_{a,b}$                               |
| ----- | ----- | ----- | ----------------- | --------- | ------------------------------- | ----------- | --------------------------------------------------------------------- | ---------------------------------------------- |
| $q_s$ | $q_1$ | $q_F$ | $\lambda \{a,b\}$ | $aba$     | $a\lambda$                      | $\emptyset$ | $\emptyset \cup \lambda\{a,b\}(aba)^* a\lambda$                       | $\{a,b\}(aba)^* a$                             |
| $q_s$ | $q_1$ | $q_4$ | $\lambda \{a,b\}$ | $aba$     | $b\cup a\{a,b\} \cup ab\{a,b\}$ | $\emptyset$ | $\emptyset \cup \lambda \{a,b\}(aba)^* b\cup a\{a,b\} \cup ab\{a,b\}$ | $\{a,b\}(aba)^* b\cup a\{a,b\} \cup ab\{a,b\}$ |
![[Pasted image 20250609001330.png]]
5) Rip $q_4$

| a     | r     | b     | $R_{a,r}$                                      | $R_{r,r}$   | $R_{r,b}$ | $R_{a,b}$         | $R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}$                             | $R^\prime_{a,b}$                                                    |
| ----- | ----- | ----- | ---------------------------------------------- | ----------- | --------- | ----------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| $q_s$ | $q_4$ | $q_F$ | $\{a,b\}(aba)^* b\cup a\{a,b\} \cup ab\{a,b\}$ | $\emptyset$ | $\lambda$ | $\{a,b\}(aba)^*a$ | $\{a,b\}(aba)^*a \cup \{a,b\}(aba)^* b\cup a\{a,b\} \cup ab\{a,b\}$ | $\{a,b\}(aba)^*a \cup \{a,b\}(aba)^* b\cup a\{a,b\} \cup ab\{a,b\}$ |
Finally, after ripping off our last state we result in:
![[Pasted image 20250609002426.png]]




