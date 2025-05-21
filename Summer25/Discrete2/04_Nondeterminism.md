### Nondeterministic Finite Automata
A **Nondeterministic Finite Automata (NFA)** is similar to a [[03_Finite Automata]] except there are a few key differences between NFA and DFA:
- NFA can have **more than one** possible transition per start per input symbol.
- **Doesn't have to have a transition for every state** for every input symbol.
- **Can transition** on the empty string $(\mathbf{\emptyset})$
Furthermore, unlike DFA, **acceptance is nondeterministic:**
- DFA accepts if the path for the input string ends on an accept state;
- HOWEVER, NFA accepts if **any** path for the input string ends on an accept state.

A **Nondeterministic FInite Automata (NFA)** is defined as a 5-tuple that is very similar to DFA:
$$
\begin{equation}\tag{NFA}
NFA = (Q,\Sigma,\delta,q_0,F) \;\;
\text{Where:}
\end{equation}
$$
- $Q\Rightarrow$ Finite set of *states*.
- $\Sigma \Rightarrow$ Finite set of symbols that create the *alphabet*.
- $\delta = Q\times \Sigma \rightarrow P(Q) \Rightarrow$ Represents the *transition functions* from the separate states.
- $q_0 \in Q \Rightarrow$ The start state of the system.
- $F\subseteq Q\Rightarrow$ A set of Final states.

### Computation in an NFA
The easiest way to think of how an NFA works is a **threaded** DFA
- Everytime there is a choice of more than one path, the NFA **splits** off a copy of itself to follow each path.
	- Copies conceptually run in parallel.
- A copy that reaches the end of input either accepts or rejects normally.
- A copy that reaches a symbol it cannot transition causes the system to enter the **dead configuration.**
	- The dead configuration is a configuration caused when a state receives a symbol that it does not have a transition function for.
	- This configuration immediately stops the system without further action.

### The Equivalences of NFAs and DFAs
To prove both Nondeterministic and Deterministic Finite Automatas are equivalent; it suffices to show that:Automatas
- $\mathbf{\forall}$ DFA, an NFA can be made that recognizes the exact same language (vice versa).
	- The capabilities of NFAs are a **strict superset** of those of DFAs $\therefore$ every DFA is already and NFA.
#### Converting from $\mathbf{NFA \rightarrow DFA:}$
- Keep in mind the observations about the computation process of an NFA:
	1) Multiple transitions imply that at any given time, an NFA is in a set of states
		- Meaning that there are multiple transition states for an NFA and that it can 'split' and create copies of the NFA to do computations in parallel/
	2) Empty transitions are handles in computation by *including their possibilities* in the set of states.
		- 
	3) Missing transitions simply don't add anything to the next set of states.
		- If there is no transition that corresponds with the symbol that is inputted to the system in the current state then the system will undergo the **dead configuration** and stop the system; meaning that this missing transition will not add anything to the next set of states.
	4) On a given transition, an NFA is simply transitioning from one element of $P(Q)$ to another.
		- This means that an NFA transitions from one element of $P(Q_0) \rightarrow P(Q_k)$ simply using the **next input symbol**. 
- $\therefore$ while an NFA is computing, we have a finite set of states that the NFA can be in, as well as a way to know which state it will end up in given only its current state and the input symbols.
#### Example: Converting $\mathbf{NFA \rightarrow DFA}$:
**Goal:** Build a DFA $(D)$ that simulates the following NFA $(N)$:
![[2025-05-19-174841_129x93_scrot.png]]
1) To begin I will define the 5-tuple definition for both the DFA & NFA:
$$
\begin{equation}\tag{DFA}
D=({Q_D},{\Sigma},{\delta_D},{q_{0D}},{F_D})
\end{equation}
$$
$$
\begin{equation}\tag{NFA}
N=({Q_N},{\Sigma},{\delta_N},{q_{0N}},{F_N})
\end{equation}
$$
	- We trying to define correct conversions for the following:
		- The finite set of states: $Q_N \rightarrow Q_D$
		- The transition function: $\delta_N \rightarrow \delta_D$
		- The start state: $q_{0N}\rightarrow q_{0D}$
		- The set of final states: $F_N \rightarrow F_D$
		- **NOTE:** The alphabet will always remain the same for this transition.
2) **States Set:**
	- To create the states set for a DFA from a NFA; simply set the DFA state set equal to the power set of the NFA state set:
		- $Q_D = P(Q_N)$
			- $Q_N=\{\emptyset,1,2,3\}$
			- $Q_D=P(Q_N)=\{\emptyset,1,2,3,12,23,13,123\}$
3) **Starting State:**
	- 