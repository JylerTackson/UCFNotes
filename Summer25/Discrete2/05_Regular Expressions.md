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

- The **starting state** will be the same as the one from the NFA; for example:
	- The starting state in the NFA is $q_1 \therefore$ starting state in the DFA is $q_1$
- The **final state** is every DFA state that includes the NFA final state; for example:
	- The final state in the NFA is $q_3 \therefore$ final state in the DFA is $\{q_3, q_{13}, q_{23}, q_{123}\}$.
- 