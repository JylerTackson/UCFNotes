Topics we will cover in the class:
1) Automata Theory
	1) Why are they important and useful?
2) Compatibility Theory
	1) Why are some problems just not solvable?
3) Complexity Theory
	1) What makes some problems hard and others easy?

# Sets
Containment:
- $x\in A$
- $x\notin A$
- $A={x,y}$
- $A={x|x\in N,x>50}$ 
Operators:
- $A\cup B$
- $A\cap B$
- $\compliment{A}$
Subsets:
Common Sets:

# Sequences

# Functions
- One-to-one
- Onto
- Bijection

# Relations
- Properties
	- Reflexive
	- Symmetric
	- Transitive

# Graphs
- Un-directed Graphs
- Paths
- Cycle
- Trees
- Directed Graphs
	- Using Binary Relations
	This binary relationship can be represented in a directed graph.

| beats    | Scissors | Paper | Rock  |
| -------- | -------- | ----- | ----- |
| Scissors | False    | True  | False |
| Paper    | False    | False | True  |
| Rocks    | True     | False | False |


# Strings
An alphabet is a non-empty finite set of symbols.

# Proofs !!!
- Definitions
	- Describe the mathematical objects and ideas
- Statements/Assertions
	- Things we say about math
- Proofs are unassailable logical demonstrations
- How to prove something:
	1) Understand the statement
	2) Convince yourself on your stance
	3) Work out its implications
	4) Break down any sub-
	5) cases you will need
	6) Start. 
- Types of Proofs:
	- Direct Argument
	- Construction
	- Contradiction
	- Weak Induction
		- We **only** assume that the particular statement holds at the k-th step. 
		**Induction Example:**
		$$
		\begin{equation}\tag{Ex 1.}
		S_n=\sum_{i=1}^ni=
		1+2+3+...+n=
		\frac{n(n+1)}{2}
		\end{equation}
		$$
		Show that $S_n=\frac{n(n+1)}{2}$ for all $n=1,2,...$
		
		1) Start with Base Case:
			 - Our **Base Case** can be something like $n=0||1||etc...$ 
			 - We must prove this initial value:
				$$
				\begin{equation}
				S_{n=1}=\sum_{i=1}^1=1=\frac{1(1+1)}{2}=\frac22=1
				\end{equation}
				$$
		$$\therefore \text{Basecase n=1 proven}$$
		2) Inductive Step:
			- Proves that if a statement holds true for some arbitrary value $k$ then it holds true for $k+1$.
				$$
				S_n={k}=\sum_{_i=1}^{k}=1+2+3+...+k=\frac{k(k+1)}{2}
				
				$$
		3) 
	- Strong Induction
