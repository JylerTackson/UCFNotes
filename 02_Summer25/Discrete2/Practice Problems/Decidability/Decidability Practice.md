### Question 1 - DFA

Consider the following language:
$$A_{DFA}=\{<B,s>|B\text{ is a DFA that accepts input string } s\}$$
Show that $A_{DFA}$ is a decidable language.
$$\text{ANSWER}$$
We are going to create a Turing Machine $(M_{DFA})$ that simulates the given DFA $(B)$.

$M_{DFA}$: on input $<B,s>$
1) Simulate $B=(Q_D, \Sigma_D, \delta_D, q_{0D}, F_D)$
2) If the simulation ends on an accepting state, accept; otherwise reject.

---
### Question 2 - NFA

Consider the following language:
$$A_{NFA}=\{<B,s>|B\text{ is a NFA that accepts input string }s\}$$
Show that $A_{NFA}$ is a decidable language.
$$\text{ANSWER}$$
We are going to create a Turing Machine $(M_{NFA})$ that simulates the give NFA ($B$)

$M_{NFA}$: on input $<B,s>$
1) Translate the given $NFA$ to a $DFA$ using the procedure taught in class.
	- We will now have $B_{DFA}$
2) Run $B_{DFA}$ on $M_{DFA}$ from question 1.
3) If $A_{DFA}$ Accepts then accept; else, reject.

---
### Question 3 - REGEX

Consider the following language:
$$A_{REX}=\{<R,s>|R\text{ is a regular expression that generates string }s\}$$
Show that $A_{REX}$ is a decidable language.
$$ANSWER$$
We are going to create a Turing machine ($M_{REX}$) that simulates the given REGEX $(REX)$:

$M_{REX}$: on input $<R,s>$
1) Translate the given $REGEX$ to an $NFA$ using the $REGEX \to NFA$ procedure
	- This will return $B_{NFA}$ - An NFA that simulates the REGEX provided
2) Now run $B_{NFA}$ on the TM $M_{NFA}$ shown in question 2.
3) If it accepts, accept; else, reject.

---
### Question 4 - Emptiness

Consider the following language that determines emptiness:
$$E_{DFA}=\{<A>|A\text{ is a DFA and L(A)=}\;\emptyset\}$$
Show that $E_{DFA}$ is a decidable language.
$$\text{ANSWER}$$
We are going to create a Turing machine ($M_\emptyset$) that is going to analyze the given DFA $(A)$ and evaluate if accepting states are reachable from the start state:

$M_\emptyset$: on input $<A>$
1) Mark the start state of the DFA
2) Traverse the DFA and continue marking new states until there are no new states:
3) If an accept state is marked, reject; otherwise, accept.

It an accept state was marked that means we were able to reach an accept state from the start state $\therefore$ the DFA $A$ produces a language and $L(A)\neq\emptyset$.

---
### Question 5 - Equivalency

Consider the following language that determines equivalency:
$$EQ_{DFA}=\{<A,B>|\text{A and B are DFAs and L(A)=L(B)}\}$$
Show that $EQ_{DFA}$ is a decidable language.
$$ANSWER$$
Recall the **symmetric difference $(A\; \triangle \;B)$:**
- $(A\; \triangle \;B)=(A-B)\cup(B-A)$


$EQ_{DFA}$: on input: $<A,B>$
1) Construct $D_C$  where $D_C=(A\; \triangle \;B)=(A-B)\cup(B-A)$.
2) Determine if $L(D_C)=\emptyset$. Accept if so, else, reject.

If two sets are equivalent, the DFA created by their **Symmetric Difference** will create empty languages.

---

### Question 6 - CFG String

Consider the following language that determines if a CFG generates a particular string:
$$A_{CFG}=\{<G,s>|\text{G is a CFG that generates the string s}\}$$
Show that $A_{CFG}$ is a decidable language.
$$ANSWER$$
We are going to create a Turing Machine $M_{CFG}$ that derives a string $s$ from the provided grammar $G$

$M_{CFG}$: on input $<G,s>$
1) Find $n=|s|$
2) Convert $G\to G_{CNF}$
3) Iterate through all derivations in $G_{CNF}$ with $2n-1$ steps
	1) It takes exactly $n-1$ steps to generate $n$ variables
	2) Then exactly $n$ steps to convert $n$ variables $\to$ terminals
4) If any iterations generate $s$ accept; else, reject

If provided with a CFG and trying to show that it is decidable that it generates a CFG, you must transfer that CFG $\to$ CNF then iterate over it in $2n-1$ steps until you either do or don't generate the string $s$.

---

### Question 7 - CFG Emptiness

Consider the following language that determines if a CFG generates an empty string:
$$E_{CFG}=\{<G>|\text{G is a CFG and L(G) =}\;\emptyset\}$$
Show that $E_{CFG}$ is a decidable language.
$$ANSWER$$
We are going to create a Turing Machine $M_{CFG}$ that derives a string from the provided grammar $G$.

$M_{CFG}$: on input $<G>$
1) Mark all the terminal symbols in $G$.
2) Repeat until no new variables get marked
	1) Iterate over every rule where a terminal produces a terminal 
		- $A\to R$
	2) If every symbol in $R$ is marked then mark $A$
3) Once all variables you can reach by working backwards are marked:
	- If the start variable is marked
		- Reject
	- Else
		- Accept

By working backwards, you are checking if you are able to reach the start variable from the terminals. The terminals are self derived and immediately provide that $G\neq \emptyset$. If you are able to reach the start variable then that shows the the start variable can reach a terminal and $L(G)\neq \emptyset$.

---

### Question 8 - ALL*

Consider the following language:
$$ALL_{DFA}=\{<A>|\text{A is a DFA and L(A) = }\Sigma^*\}$$
Show that $ALL_{DFA}$ is a decidable.
$$ANSWER$$
We are going to create a TM $M_{A_{DFA}}$ that simulates a DFA that is the complement of $A$.
$M_{A_{DFA}}$: on input $<A>$
1) Construct the complement DFA of $A\to \bar{A}$
2) Simulate $\bar{A}=\{Q_{D}, \Sigma_D, \delta_D, q_{0D}, F_D\}$
3) Using $M_\emptyset$ from Question 4, find if $\bar{A}=\emptyset$
	- If $M_\emptyset$ Accepts; Accept
	- Else; Reject

To solve if a DFA is able to produce a language that contains the set of the entire alphabet that is start closured you will simply need to create a DFA that is the complement of itself and solve if that one derives the language that contains only emptiness.

---

### Question 9 - $\lambda$
Consider the following grammar:
$$A\lambda_{CFG}=\{<G>|G\text{ is a CFG that generates }\lambda\}$$
Show that $A\lambda_{CFG}$ is a decidable.
$$ANSWER$$
We are going to create a TM $M_\lambda$ that checks to see if we can derive $\lambda$ from the given grammar $G$.

Recall:
- If we are searching for the string $s=\lambda$
	- $|s|=0$

$M_\lambda$: on input $<G>$
1) Convert $G\to G_{CNF}$
2) We are searching to check if G generates $\lambda \therefore s=\lambda$ & $|s|=0=n$ 
3) Iterate through all derivations in $G_{CNF}$ with $2n-1$ steps
	1) It takes exactly $n-1$ steps to generate $n$ variables
	2) Then exactly $n$ steps to convert $n$ variables $\to$ terminals
4) If any iterations generate $s$ accept; else, reject

This problem can be accomplished very similar to problem #6, here we are utilizing the idea of all derivations in a $G_{CNF}$ take $2n-1$ steps and with our $n=0$ we should be able to generate $\lambda$ in 0 steps (at the starting variable).

---

### Question 10 - Turing Recognizable

Consider the following set of Turing Machines:
$$E_{TM}=\{<M>|M\text{ is a Turing Machine and L(M) = }\emptyset\}$$
Show that $\overline{E_{TM}}$ is Turing Recognizable
$$ANSWER$$
Recall:
- Being Recognizable and Decidable are different things
	- Decidable
		- I can always give a correct yes/no answer in finite times
		- Every Decidable language is Recognizable.
	- Recognizable
		- I can eventually confirm yes/no instances

