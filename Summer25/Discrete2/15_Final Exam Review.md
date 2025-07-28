Based on the Final Exam Review Topics given by Steinberg:
1) Context Free Grammar `- Grammar`
2) S-Grammar `- Grammar`
3) Grammar Ambiguity `- Grammar`
4) Removing Lambda Productions `- Grammar`
5) Remove Unit-Production `- Grammar`
6) NPDA
7) Turing Machine
8) Decidability
9) Decidability
10) Polynomial Run Time
11) **T-F:** 3SAT
12) **T-F**: Cook-Levin Theorem
13) Turing Machine


## Topic 1: Grammar
There are three types of grammars that we will focus on; there are also several rules for Grammar that are pertinent to study:
1) Context Free Grammar
	1) Linear Grammar
	2) Grammar Ambiguity
2) Simple Grammar
3) Chomsky Normal Form Grammar
	1) Removing Lambda Production
	2) Removing Unit Rules

### Context Free Grammar (CFG)
Grammar is a mechanism to describe a language, it is a quadruple defined as:
$$G=(V,\Sigma,R,S)$$
Where:
- $V\to$ Variables
- $\Sigma\to$ Terminals
- $R\to$ Rules
- $S\in V\to$ Start Variable

#### Linearity
A grammar produces a **regular language** if we have only one variable per production and we DO NOT mix left and right linearity.
1) Right Linear
	- All rules and productions are on the right side:
		- $A\rightarrow xB$
		- $A\rightarrow x$
2) Left Linear
	- All rules and productions are on the left side:
		-  $A\rightarrow Bx$
		- $A\rightarrow x$

#### Ambiguity 
Ambiguity is defined in the book as:
"A string $w$ is derived **ambiguously** in CDG $G$ if it has two or more different leftmost derivations. $G$ is **ambiguous** if it generates some string **ambiguously**."

#### Simple Grammar (S-Grammar)
A simple Grammar is a form of $CFG$ if all the rules are of the following form:
$$A\to\alpha x$$
Where:
- $\alpha \in \Sigma$
- $x\in V^*$
This grammar is a much more strict form of grammar that helps prevents ambiguity.

#### Chomsky Normal Form Grammar (CNF)
A CFG $G$ is in $CNF$ form if every rule has one of the following forms:
1) $A\to BC$
2) $A\to a$
Where:
- $a\to$ any terminal
- $A,B,C\to$ any variables
	- $B,C\neq S$

To transfer a $CFG\to CNF$ it is a simple 4 step process:
1) Add a new start variable: $S^\prime$
2) Get rid of rewrites to $\lambda$
	- This can be done by tracing the variable to $\lambda$ and replacing it with the possible productions
3) Get rid of unit rules
	- This can be done by replacing the rule on the right side with what it produces
4) Convert all the remaining rules to conform to the $CNF$ form
	- This can be done by adding in new variables that are single terminal transitions.


---

## Topic 2: DFA and NFA
I am going to review the definitions of a $DFA$ & $NFA$ as well as several important key notes.

### DFA
A $DFA$ **(Deterministic Finite Automata)** is a 5-tuple that is defined as the following:
$$DFA=(Q,\Sigma,\delta,q_0,F)$$
Where:
- $Q\to$ Set of States
- $\Sigma\to$ Alphabet
- $\delta \to$ Transition Function
- $q_0 \to$ Start State
- $F \to$ Set of Accept States

### NFA
Similarly to the $DFA$, an $NFA$ (Nondeterministic finite automaton) is a 5-tuple that is defined as the following:
$$NFA=(Q,\Sigma,\delta,q_0,F)$$
Where:
- $Q\to$ Set of States
- $\Sigma\to$ Alphabet
- $\delta \to$ Transition Function
- $q_0 \to$ Start State
- $F \to$ Set of Accept States

#### NFA $\to$ DFA
Its important to know that every $NFA$ can be converted to a $DFA$
1) Define the $Q_N \to Q_D$
	-  $Q_D = P(Q_N)$; The states of the $DFA$ are the powerset of the states in the $NFA$.
2) Defined $F_N \to F_D$
	- Every state number within $Q_D$ that includes the $F_N$ number will now also be in the set $F_D$
3) Defined $q_{0_{N}}\to q_{0_{D}}$
	- Any state number within $Q_D$ that includes the $q_{0_{N}}$ can be defined as $q_{0_{D}}$
4) Defined $\delta_N \to \delta_D$
	- Create a transition function table going through all $\delta_N$ and applying those transitions to $\delta_D$

---

## Topic 3: GNFA's
A $GNFA$ is a special kind of $NFA$ that uses regular expressions as its transition alphabet.
- A $GNFA$ has a **single start state** and a **single accept state**.

To create out $GNFA$ we will continuously "rip and repair" states while utilizing a formula that works regardless of the provided $DFA$:
$$R^{\prime}_{a,b}=R_{a,b}\cup R_{a,r}(R_{r,r})^*R_{r,b}$$

---
## Topic 4: Pumping Lemma (Non-Regular Language)
F in DFA and NFA stands for **FINITE** its important that we are able to have a finite amount of states in order for a language to be **regular**. 

### Pumping Lemma
Pumping lemma is a way to prove that a language is not regular. This proof is a **BWOC** where we must assume that the language $(L)$ is regular and then disprove it by either pumping in or out of the language. Your goal in the pumping lemma is to contradict the language provided which will prove that the language is not a regular language.

If $L$ is a regular language, then there is a number $p$ (**pumping length**), s.t. if $s$ is a string in $A$ with length of at least $p$ then $s=xyz$ s.t.:
- $xy^iz$ is a string in $L$ for all $i\geq0$
- $|y| > 0$
- $|xy| \leq p$
Notes:
- $x$ and $z$ can be empty, but $y$ CANNOT. This is the whole idea of the P.L.

I will demonstrate the pumping lemma through an example:

### Example:
Consider the following Language:
$$\Sigma =\{a,b\} \; \; L=\{w\in \Sigma^*: n_a(w)<n_b(w)\}$$
- Assume by contradiction that $L$ is regular.
- Pumping Lemma states there exists an integer $m > 0$ s.t $\forall \;w \in L$, $w$ can be decomposed $w=xyz$ with $|xy| \leq m$, $|y| >0$, and $w_i=xy^iz\in L$

Choose our string $w$. $w=xyz$. Since $|xy| \leq m$ and $|y| \geq 1 \Rightarrow y$ contains only a's $y=a^k$ with $k \geq 1$
$$w=a^mb^{2m}$$
$$w_i=a^{m-k}(a^k)^ib^{2m}\in L$$
Just to clarify, above we say that the Pumping Lemma defines a string w that can be decomposed s.t:
- $w=xyz$
- $w_i = xy^{i}z$
	- $a^{m-k}$
	- $y^i$ = $(a^k)^i$
	- $z=b^{2m}$

Now we can choose a value for $i$ and we can either:
- **Pump in** by choosing a positive value for $i$
- **Pump out** by choosing a negative value for $i$

---
## Topic 5: PDA - Pushdown Automata
A Pushdown Automaton is defined as follows:
$$PDA=(Q,\Sigma,\Gamma, \delta,q_0,F)$$
Where:
- $Q\to$ Set of States
- $\Sigma\to$ Alphabet
- $\Gamma \to$ Stack Alphabet
- $\delta \to$ Transition Function
- $q_0 \to$ Start State
- $F \to$ Accept State

A Pushdown Automaton is essentially a DFA that has an included memory element which is a stack. On each transition, you are able to also pop and push to a stack that helps you iterate through the PDA.

#### PDA & CFG:
PDA and CFG's are equal in power - this is important later on in **Decidability and Reduction**.
- A language is context-free if and only if a context-free grammar generates it. 
- A language is context-free if and only if a pushdown automaton recognizes it. 
- A context-free grammar generates a language if and only if a pushdown automaton recognizes it.

#### Notation:
A transition is followed by a stack notation:
- $0, \lambda\to0$
	- If we read 0, push 0 to the stack 
- $0, 0\to\lambda$
	- If we read 0, pop 0 from the stack
- $0, \lambda\to\lambda$
	- If we read 0, do nothing to the stack

Recall:
- You are able to simulate any string with as many or as little $\lambda$'s within the string
Starting:
- $\lambda, \lambda \to \$$
	- If we read $\lambda$, push the starting symbol ($) to the stack 
- $\lambda, \$\to\lambda$ 
	- If we read $\lambda$, pop the starting symbol ($) from the stack

---
## Topic 6: Turing Machines
A Turing Machine is defined as follows:
$$TM=(Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$$
Where:
- $Q\to$ Set of states
- $\Sigma\to$ Input Alphabet
- $\Gamma\to$ Tape Alphabet
- $\delta\to$ Transition Function
- $q_0 \to$ Start State
- $q_{accept}\to$ Accept State
- $q_{reject}\to$ Reject State ($q_{accept}\neq q_{reject}$)

The way a Turing Machine works is that there is a string that is located on an infinite tape. The Machine starts at the left side head of the string and infinitely left and right of the string is null characters $(\square)$. You traverse the states by reading in values from the string on the tape and moving the head of the TM Left, Right, and Staying put.

### Forms of Turing Machines
There are several forms of Turing machines that were taught in class:
1) Enumerator
2) $^{\star\star}$Multi-Tape Turing Machines$^{\star\star}$
3) Nondeterministic Turing Machines

#### Enumerator
- Loosely defined, an Enumerator is Turing machine with a printer. It generates, in some order, all the strings accepted by its language.

#### Multi-Tape
A Multi-Tape Turing Machine has a finite number of tapes each with its own read & write head.
- Input appears on tape 1 while the others are blank (full of $\square$ characters).
- On each transition we read and write to all the tapes at once.
- On each transition we move left or right on all the tapes at once.

#### Nondeterministic Turing Machines



---
## Topic 7: Decidability
There are three main topics taught in this topic:
1) Decidability of Turing machines
2) Turing Recognizability
3) Undecidability (basis for Reduction)

### Decidability
A language is Turing-Decidable if there exists a Turing Machine that halts and accepts all strings in the language and halts and rejects all strings not in language. Basically we can say that if there is a Turing Machine that we can definitively say will either halt, accept, or reject a string based on a specific language then that language is Decidable.

### Turing Recognizable
A language is Turing-recognizable if there exists a Turing Machine that accepts all strings in the language and either rejects or loops forever on strings not in the language. Basically we can say that if there is a Turing Machine that can always accept a string within the language but not definitively answer if it will reject then this language is Turing Recognizable.

### Undecidable
There will be much more covered in Topic 8: Reduction however, A language is undecidable if NO Turing Machine can decide the language. Basically if there is no Turing Machine that can correctly determine if a string belongs to a given language then that language is Undecidable.

One **VERY IMPORTANT** Turing Machine taught in this topic was the Acceptance problem for Turing Machines:
$$A_{TM}=\{<M,s>|\text{M is a Turing machine that accepts s}\}$$
Assume that it's decidable. Given that, there exists a *decider* $H$ for $A_{TM}$ that is, itself a Turing Machine s.t. $H$ run on $<M,s>$ accepts if $M$ accepts $s$ and rejects if $M$ doesn't:
$$H(<M,s>)\text{ accepts if M accepts s and rejects otherwise.}$$
Now... consider a new "*Devil's Advocate*" machine $D$. This machine takes the decider, runs it on the encoding of the original machine, and outputs the **opposite** result
$$D(<M>)\text{ accepts if } H(<M,<M>>) \text{ rejects, and rejects if it accepts.}$$
In other words:
$$D(<M>) \text{ accepts if M rejects} <M>, \text{ and rejects if M accepts }<M>$$
$D$ must run on itself causing:
$$D(<D>) \text{accepts if }D\text{ rejects} <D>, \text{ and rejects if D accepts }<D>$$
This is a clear contradiction concluding that $A_{TM}$ is undecidable.



---
## Topic 8: Reduction


---
## Topic 9: P & NP

