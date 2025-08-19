### **Lessons:**
[[02_Three Basic Concepts]]
- [[02_Three Basic Concepts#Languages]]
- [[02_Three Basic Concepts#Grammar]]
- [[02_Three Basic Concepts#Automata]]
[[03_Finite Automata]]
[[04_Nondeterminism]]

# Sets
**Containment:**
- $x\in A$
	- $x$ is **in** set $A$**Lessons:**
- $x\notin A$
	- $x$ is **not in** set $A$
- $A=\{x,y\}$
	- Set $A$ contains what is within the bracket.
		- If you see $\{a,b\}^*$ that means that the set contains all possible combinations, notated by $*$, of the contents of within the brackets.
- $A={x|x\in \mathbb{N},x>50}$ 
	- This is just notation saying that the set $A = x$ where:
		  $x$ is in the set of Natural Numbers $\mathbb{N}$ and is below 50.
**Operators:**
- $\text{Union} \Rightarrow A\cup B$
	- Creates a new set, we will call $C$, that's contents are the combination of sets $\text{A \& B}$
- $\text{Intersection} \Rightarrow A\cap B$
	- Creates a new set, we will call $C$, that's contents exclude everything that sets $\text{A \& B}$ have in common
- $\text{Complement} \Rightarrow \bar{A}$
	- 
**Subsets:**
- $A\subseteq B$
	- This statement above is saying that **A is a subset of B**; it can be thought as:
		- $\forall \; x \in A,\; x \in B$
- $A \subsetneq B$
	- This statement above is saying that **A is a proper subset of B**; it can be thought as:
		- $\forall \; x \in A,\; x\in B, \text{ and } A\neq B$
**Common Sets:**
- $\mathbb{Z}$ : Set of all integers
- $\mathbb{N}$ : Set of all natural numbers
- $\mathbb{\emptyset}$ : Empty set
---
# Sequences
- Ordered sets are thought of as sequences
- Finite Sequences are called **k-tuples**
	- **Grammar** is a finite sequence that is a **4-tuple:**
		- $\mathbf{G=(V, \Sigma, R, S)}$
	- **Discrete Finite Automata** is a finite sequence that is a **5-tuple:**
		- $\mathbf{DFA=\{Q,\Sigma,\delta,q_0,F\}}$
- **Ordered Pairs** are known as **2-tuples**
---
# Functions
- **One-to-one**
	- Maps every element of the range from **at most one** element of the domain
- **Onto**
	- Maps every element of the range from **at least one** element of the domain
- **Bijection**
	- Every element of the range is **mapped by exactly one** element of the domain.

---
# Relations
- Properties
	- Reflexive
	- Symmetric
	- Transitive

---
# Graphs
- Nodes
	- The **degree of a node** is a number of edges that connect to that node.
- Edges
	- The **weight of an edge** is the cost for the algorithm to travel across the edge.
- **Un-directed** Graphs
	- Edges are unique; you can only have ONE edge between the same pair of nodes.
	- In an un-directed graph you can traverse an edge in either direction unlike a directed graph or a tree.
	- A **simple path** doesn't repeat any nodes
	- A graph is **connected** if every two nodes have a path
- Subgraphs
	- A graph $G$ is a subgraph if it has a subset of $H$'s nodes and all related edges.
- Paths
	- **Sequence** of nodes connected by edges
- Cycle
	- A path is a cycle if it **starts and ends** on the same node.
- Trees
	- A graph is a tree if it is **connected** and has **NO simple cycles**
- Directed Graphs
	- Directed paths are paths that follow the directions of the edge
	- Directed Graphs can create paths using Binary Relations such as the one below:
	- This relationship can define a 3 node graph with directed edges.

| beats    | Scissors | Paper | Rock  |
| -------- | -------- | ----- | ----- |
| Scissors | False    | True  | False |
| Paper    | False    | False | True  |
| Rocks    | True     | False | False |
 
---
# Strings
An alphabet is a non-empty finite set of symbols.


---
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
			 - We must prove this initial value on the right side of the equation:
				$$
				 \begin{equation}\tag{Base Case}
				 S_{n=1}=\frac{1(1+1)}{2}=\frac22=1
				 \end{equation}
				 $$$$\therefore \text{Basecase n=1; Base Case holds True}$$
		2) Inductive Step:
			- Proves that if a statement holds true for some arbitrary value $k$ then it holds true for $k+1$, by showing that:$$
\begin{equation}\tag{I.S.1}
S_{(k)} \Rightarrow S_{(k+1)}
\end{equation}
$$$$
\begin{equation}\tag{I.S.2}
S_{(k)}=\sum^{k}_{i}={1 + 2 + 3 + ... +k}=
\frac{k(k+1)}{2}
\end{equation}
$$
			- To show the **Inductive Hypothesis**, add **k+1** to both sides: $$
\begin{equation}\tag{I.S.3}
{(1 + 2 + 3 + ... +k)}+(k+1)=
\frac{k(k+1)}{2}+(k+1)
\end{equation}
$$
			- $\therefore$ the equation above is showing: $S_k+(k+1)=S_k+(k+1)$
			- To prove using weak induction you show that $S_k+({k+1})=S_{k+1}$$$\begin{equation}\tag{I.S.4}(1+2+3+...+k+(k+1))=\frac{k(k+1)}{2}+\frac{2(k+1)}{2}\end{equation}$$ $$\begin{equation}\tag{I.S.5}S_{(k)}+(k+1)=\frac{k^2+3k+2}{2}\end{equation}$$
			- $\therefore S_{k} + (k+1)=S_{k+1}$ **Which proves using weak induction.** 
	- Strong Induction


