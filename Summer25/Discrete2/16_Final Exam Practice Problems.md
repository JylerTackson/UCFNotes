# 1) Decidability

### 1) $A_{DFA}$
$$A_{DFA} = \{<B,s> | \text{ B is a DFA that accepts input string s}\}$$
Show that $A_{DFA}$ is a decidable language
$$ANSWER$$
To show that $A_{DFA}$ is a decidable language I will create a Decider $M$.

$M:$ on input $<B,s>$
1) Create a variable $n=|s|$
2) Simulate $B$ on $M$ using $s$
	1) If after $n$ steps we are on an accepted state, accept.
	2) Else, Reject.

---
### 2) $A_{NFA}$
$$A_{NFA}=\{<B,s>|\text{ B is a NFA that accepts input string s}\}$$
Show that $A_{NFA}$ is a decidable language
$$ANSWER$$
To show that $A_{NFA}$ is a decidable language I will create a Decider $M$.

$M:$ on input $<B,s>$:
1) Transfer $B$ to a DFA using the $NFA \to DFA$ procedure
2) Simulate $<B,s>$ on the Decider created in problem 1 for $A_{DFA}$, we will refer to it as $M_1$
	1) If $M_1$ accepts, accept
	2) If $M_1$ rejects, reject

---
### 3) $A_{REX}$
$$A_{REX}=\{<R,s> | \text{ R is a regular expression that generates string s}\}$$
Show that $A_{REX}$ is a decidable language:
$$ANSWER$$
To show that $A_{REX}$ is a decidable language I will create a Decider $M$

$M:$ on input $<R,s>$
1) Convert $R$ to a $NFA$ using the $GNFA$ process
	1) Now we know that $R$ is an $NFA$ that accepts our regular expression $s$.
2) Simulate $R_{NFA}$ on the Turing Machine created in problem 2, we will call it $M_1$
3) If $M_1$ accepts, accept
4) If $M_1$ rejects, reject

---

### 4) $E_{DFA}$
$$E_{DFA}=\{<A> | \text{ A is a DFA and L(A)}=\emptyset\}$$
Show that $E_{DFA}$ is a decidable language.
$$ANSWER$$
To show that $E_{DFA}$ is a decidable language I will create a Decider $M$

$M:$ on input $<A>$
1) Transfer $DFA$ to a $G$
2) Since we are searching for $\emptyset$, we create a variable of $n=|s|=0$
3) Traverse the grammar from the start state:
	1) if after $2n-1$ steps you have not created $s$, reject
	2) else, accept

---

### 5) $EQ_{DFA}$

$$EQ_{DFA}=\{<A,B> | \text{ A and B are DFAs and }L(A)=L(B)\}$$
Show that $EQ_{DFA}$ is a decidable language.
$$ANSWER$$
To show that $EQ_{DFA}$ is a decidable language I will create a Decider $M$

Recall:
- Symmetric Difference: $A\triangle B = (A \cup B)-(A\cap B)$
	- The set of elements that are in either _A_ or _B_, but not in both.

$M:$ on input $<A,B>$
1) Create a DFA $C=A\triangle B$
	1) If $C = \emptyset$, accept
	2) else, reject

---

###  6) $A_{CFG}$
$$A_{CFG}=\{<G,s> | \text{ G is a CFG that generates the string s}\}$$
Show that $A_{CFG}$ is a decidable language.
$$ANSWER$$
To show that $A_{CFG}$ is a decidable language I will create a Decider $M$:

$M:$ on input $<G,s>$
1) Create a variable $n=|s|$
2) Translate $G$ into a Chomsky Normal Form Grammar.
	1) $G\to G_{CNF}$
3) Starting at the start variable, simulate $G_{CNF}$
	1) If after $2n-1$ steps you are able to generate $s$; accept.
	2) else, reject.

---

# 2) Reduction

### 1) $HALT_{TM}$
$$HALT_{TM}=\{<M,w> | \text{ M is a TM and M halts on input w}\}$$
Show that $HALT_{TM}$ is undecidable.
$$ANSWER$$
To show that $HALT_{TM}$ is undecidable I am going to prove BWOC by creating a decider $M_{HALT}$ and simulating $HALT_{TM}$ on $M$

$M_{HALT}:$ on input $<M,w>$:

1) Create an instance of $A_{TM}$ called $M_1$
2) Simulate $M$ on $M_1$: on input $<M,w>$
	1) $A_{TM}$ is an undecidable $TM$ and assumes that $w$ is a string accepted by $M$
3) If $M_1$ accepts, accept
4) else, reject

Since we must use an undecidable $TM$ to simulate this, we can conclude that the $HALT_{TM}$ is undecidable.

---

### 2) $E_{TM}$
$$E_{TM}=\{<M>| \text{M is a TM and }L(M)=\emptyset\}$$
Show that $E_{TM}$ is undecidable
$$ANSWER$$
To show that $E_{TM}$ is undecidable I am going to prove BWOC by:
- Creating a decider for $E_{TM}$ called $M_1$

$M_1:$ on input $<M>$

1) Create a Turing Machine $M_2$ where:
	- $M_2:$ on input $<M>$
		- Mark the start state
		- Starting at the start state, traverse and mark all new states
		- If you are able to reach an accept state, accept
		- Else, Reject

2) Simulate $M_2$ on $M_1$
	- If $M_2$ accepts, reject
	- Else, accept


---

### 3) $REGULAR_{TM}$
$$REGULAR_{TM}=\{<M>| \text{M is a TM and }L(M)\text{ is a regular language}\}$$
Show that $REGULAR_{TM}$ is undecidable.
$$ANSWER$$
To show that $REGULAR_{TM}$ is undecidable I am going to prove BWOC by:
- Creating a Decider for $REGULAR_{TM}$ called $M_1$
- Creating a Decider for $A_{TM}$ called $M_2$

$M_2$: on input $<M,w>$

1) If $M_2$ rejects, reject
2) If $M_1$ accepts, simulate $M_1$ on input $<M>$
	1) Create a $CFG$ that generates strings within $L(M)$ we will call it $G$
	2) Transfer $G\to G_{CNF}$
	3) Create a Turing Machine $M_3$ where:
		- $M_3$: on input $<G,w>$
			- $n=|s|$
			- Generate a string in $2n-1$
			- If the generated string $=s$, accept
			- Else, Reject
	4) Simulate $M_3$ on $M_1$
		- $M_1$: on input $<M_3>$
	5) If $M_3$ accepts, accept
	6) Else, Reject.


Using this technique, we are using the $A_{TM}$ machine, which we know is undecidable to determine if a given string $w$ is within the regular language. This shows that $REGULAR_{TM}$ is undecidable.
