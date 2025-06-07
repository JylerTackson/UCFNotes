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
		- Meaning that there are multiple transition states for an NFA and that it can 'split' and create copies of the NFA to do computations in parallel.
	2) Empty transitions are handles in computation by *including their possibilities* in the set of states.
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


# What is a Regular Language?
- As long as a DFA can recognize a language then it is considered a Regular Language.
- A union between regular language results in a regular language.

- Every NFA has an Equivalent DFA.
	- Every DFA by default is an NFA.
	- Not every NFA is a DFA due to rule violations but can be CONVERTED to an equivalent DFA's.

- Convert the following NFA into its equivalent DFA:
![[2025-06-02-141348_472x138_scrot.png]]

1) Defining your set of states for you DFA.
	- Your DFA set of states will be constructed of the **Power Set** of your NFA's sets.
**For Example:** The above NFA has 3 states $\{1,2,3\} \therefore$ the DFA state set will be $P\{1,2,3\}=\{1,2,3,12,13,23,123,\emptyset\}$

- The **starting state** will be the same as the one from the NFA; for examp,.,le:
	- The starting state in the NFA is $q_1 \therefore$ starting state in the DFA is $q_1$
- The **final state** is every DFA state that includes the NFA final state; for example:
	- The final state in the NFA is $q_3 \therefore$ final state in the DFA is $\{q_3, q_{13}, q_{23}, q_{123}\}$.

#### How an NFA reads a string?
It is important to understand how a string is parsed into an Finite Automata. The string is defined as a set of symbols from the alphabet. The alphabet includes a symbol known as the null symbol $(\lambda)$ which effects how the string is parsed to the finite automata.
- When a string is read it can be seen as:
	- $w=\lambda^n S \lambda^n$
- This is saying that you can have an $n$ number of null symbols at both the beginning and the end of the string with the symbols from your alphabet $(S)$ in the middle.

#### Defining transition functions for a DFA:
Now that we understand how many states will be within our DFA from the NFA & how strings are properly parsed into finite automatas we can start defining the transition functions which define the relationships between the nodes within the DFA.

Transition Functions $\delta_D$:
- $\delta(q_1,a)= \{q_1,q_2,q_3\}=q_{123}$
- $\delta(q_1,b)=\{q_\emptyset\}=q_\emptyset$
- $\delta(q_2,a)=\{q_3\}=q_3$
- $\delta(q_2,b)=\{q_2,q_3\}=q_{23}$
- $\delta(q_3,a)=\{q_3\}=q_3$
- $\delta(q_3,b)=\{q_\emptyset\}=q_\emptyset$

Now that we have defined our transition functions for our single states, the rest of the transition 
- $\delta((q_1,q_2),a)=\delta(q_1,a)\cup\delta(q_2,a)=\{q_1,q_2,q_3\}\cup\{q_3\}=q_{123}$
- $\delta((q_1,q_2),b)=\delta(q_1,b)\cup\delta(q_2,b)=\{q_\emptyset\}\cup\{q_2,q_3\}=q_{23}$
- $\delta((q_1,q_3),a)=\delta(q_1,a)\cup\delta(q_3,a)=\{q_1,q_2,q_3\}\cup\{q_3\}=q_{123}$
- $\delta((q_1,q_3),b)=\delta(q_1,b)\cup\delta(q_3,b)=\{q_\emptyset\}\cup\{q_\emptyset\}=q_\emptyset$
- $\delta((q_2,q_3),a)=\delta(q_2,a)\cup\delta(q_3,a)=\{q_3\}\cup\{q_3\}=q_3$
- $\delta((q_2,q_3),b)=\delta(q_2,b)\cup\delta(q_3,b)=\{q_2,q_3\}\cup\{q_\emptyset\}=q_{23}$
- $\delta((q_1,q_2,q_3),a)=\delta(q_1,a)\cup\delta(q_2,a)\cup\delta(q_3,a)=\{q_1,q_2,q_3\}\cup\{q_3\}\cup\{q_3\}=q_{123}$
- $\delta((q_1,q_2,q_3),b)=\delta(q_1,b)\cup\delta(q_2,b)\cup\delta(q_3,b)=\{q_\emptyset\}\cup\{q_2,q_3\}\cup\{q_\emptyset\}=q_{23}$

Utilizing the above transition statements we can construct the DFA as followed:
![[2025-06-05-172906_460x493_scrot.png]]
In the DFA you notice that starting at $q_1$ you are **UNABLE** to reach the states: $\{q_{12}, q_{13}, q_2\}$. These states can be removed from the final DFA due to them having no affect on the final state of the actual system resulting in:
![[2025-06-05-173511_460x492_scrot.png]]