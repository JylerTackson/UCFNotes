A Finite Automaton are good models for computers with extremely limited memory. You must define specific actions that put the computer into states to carry out goals by the system; that is where the topic of Discrete Finite Automata comes in. DFA is a 5-tuple that consists of:
- $Q \Rightarrow$A finite set of states
	- A **state** can be thought of as a position in which the system can be in.
		- If your system is a door your states are $\{open, closed\}$
- $\Sigma \Rightarrow$An alphabet
- $\delta: Q\times\Sigma \rightarrow Q\Rightarrow$ A transition function
	- This is a function that defines how the system transitions from one state to another.
- $q_o \in Q\Rightarrow$ A start state
	- This is the initial state of the system as a whole. 
- $F \subseteq Q\Rightarrow$ A set of accept (or final) states
	- This is the final state that the system will end up in after the start state undergoes the specific transition function.
**NOTE:** $q_o \; \text{and} \; F$ are relative to the **current state** of the system.

## Example 1:
![[2025-05-17-094028_462x191_scrot.png]]
The finite automaton above, which we will notate as $M_1$, can be describe using the formal definition of an automaton $\Rightarrow M_1=(Q,\Sigma,\delta,q_o,F)$, where:
- $Q=\{q_1, q_2, q_3\}$
- $\Sigma=\{0,1\}$
- $\delta$ which is the transition function, can be described such as:

|       | 0     | 1     |
| ----- | ----- | ----- |
| $q_1$ | $q_1$ | $q_2$ |
| $q_2$ | $q_3$ | $q_2$ |
| $q_3$ | $q_2$ | $q_2$ |
- $q_1$ is the start state
	- This can be seen from the arrow coming into $q_1$ from the left hand side of the image.
- $F=\{q_2\}$ 
	- This can be seen from the double circle around $q_2$

