# Homework 2 - 60pts
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


## 2. RegEx
15 points) In the C programming language, a value can be designated as a character type through a declaration statement where the prefix starts with char and ends with the suffix ;. Between the prefix and suffix is the name of the variable. Let C be the language of valid character declaration statements. A member of C must start with char and end with ;. The member must have at least 2 characters in its variable name and cannot contain the ; character. For example, the statement `char nums;` is valid since nums has 4 characters, but `char x;` is not valid since x is only one character. For simplicity, assume that the alphabet for C is $\Sigma = \{a, b, c, d, e, h, i, r, ; \}$. Give a regular expression that generates C. You cannot use the set difference when creating your regular expression. Please write out the possible set of symbols that can be generated.

Restrictions:
- Must start with the prefix: `char`
- Must contain **at least** 2 characters within $\Sigma$ (excluding $;$)
- Must end with the suffix: `;`
- Can NOT use set difference.

$r_C=char\{a | b | c | d | e | h | i | r\}^n; \text{ Where n }\geq 2$
- This expression satisfies the requirements
	1) Concatenates the preffix `char`
	2) Uses every valid symbol from alphabet
		- Excludes `;`
		- Includes all symbols by using the `|` OR operation
	3) Specifies that $n\geq2$ which satisfies the length requirement
	4) Finally Concatenates the suffix `;`

## 3. Proof by Construction
(15 points) Let A and B be regular languages. We define the following operation PSHUFFLE. 

PSHUFFLE(A,B) = {w | w = a1b1...akbk, where a1...ak ∈ A and b1...bk ∈ B, each ai, bi ∈ Σ}. 

Show that the class of regular languages is closed under PSHUFFLE. You will need to write out a proof. Hint, use a proof by construction technique.