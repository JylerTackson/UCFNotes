**Directions:** Answer each of the questions to the best of your ability. Make sure to show
your work in order to receive potential FULL credit. Just stating the answer will result
in point deductions (and possibly no credit for the respective problem) and that cannot be
disputed through the grade dispute policy. Your answers must typed up and submitted as a
PDF. Handwritten solutions will not be accepted. Please note that you can create a separate
document when designing your solutions. You do not need to fit your answers in the spaces
between each question.

---
# 1) Useless States (10 Points)
A ***useless state*** in a pushdown automata is never entered on any input
string. Consider the problem of determine whether a pushdown automata has any
useless states. Formulate this problem as a language and show that it is **decidable**.
- Hint: Think about some of properties we learned about context-free grammars.
$$ANSWER$$
1) Formulate the problem as a language
	- We are trying to show that there is a $PDA$ $(P)$ that contains useless. The language can be defined as:
	$$L_{PDA}=\{<P>|\text{P is a PDA that may or may not contain useless states}\}$$
	- We must show that this language is decidable.
		- There exists a Turing machine that can decide if $P$ has a useless state.
	- When we consider:
		- PDA states are finite
		- PDA transition functions are finite
	- We can easily create a Turing machine that can traverse the entire PDA and evaluate each state and determine if one is unreachable.

To figure out if this is Decidable, we will construct a Turing machine $(M_{PDA})$ that will simulate our PDA and find any unmarked states.
$M_{PDA}:$ on input $<P>$
1) Enumerate all states $q\in Q(P)$
2) For each $q$
	1) Build the PDA $P_q$
	2) Convert $P_q$ into a $CFG\to P_{CFG}$
		1) If $L(P_{CFG}) = \emptyset$, then q is useless, accept
		2) else, $L(P_{CFG})\neq\emptyset$, reject
	3) If


---

# 2) SPCP (5 Points)
In the *Silly Post Correspondence Problem*, **SPCP**, the top string in each
domino has the same length as the bottom string. Show that **SPCP** is decidable. Yes
decidable, not undecidable.
$$ANSWER$$
1) Formulate the problem as a language
	- We are trying to show that $SPCP$ is decidable. The language can be defined as:
	$$L_{SPCP}=\{<P>|\text{ Where P is an instance of the SPCP problem that has a solution.}\}$$
	- We must show that this language is decidable.
		- There exists a Turing Machine ($M_{SPCP}$) that can decide if the string on the top matches the string on the bottom.
	- Recall that we must consider attributes of the SPCP problem:
		- All dominoes have the same top and bottom string lengths $\therefore$ the top and bottom string lengths will ALWAYS remain equal.

To figure out if this is Decidable, we will construct a Turing Machine $(M_{SPCP})$ that will run the instance of the $SPCP$ problem $(P)$ and evaluate this for us:
$M_{SPCP}:$ on input $<P>$
1) Let $D=\{\frac{t_i}{b_i}\}$ be the domino set for the given $SPCP$ problem.
2) Initialize a queue for $i$ where $1 \leq i \leq |D|$
3) While the queue is not empty:
	- Dequeue the next domino in the queue
	- Construct the top and bottom strings using the dequeue domino
		- If $T=B$: **Accept**
		- Else: Do not explore this sequence of dominoes further
4) If the queue is exhausted and no match is found, **reject.**


---

# 3) Undecidable (10 Points)
Let $T = \{M\; |\; \text{M is a TM that accepts wR whenever it accepts w}\}$.
Show that T is **undecidable**.
$$ANSWER$$
Our language T is a set of all Turing Machines whose accepted language is closed under reversal.
- If M accepts "hello", then to be in the set $T$, it must also accept "olleh".

To prove by contradiction we will first have to make the assumption that the language $T$ is decidable.
1) Assume that the language $T$ is decidable:
	- Let $D_T$ be a decider for $T$.

2) Pick any fixed string $(s)$ such that it is NOT a palindrome. I am going to build a TM $M_{T}$ from any pair of $<M,w>$
	$$M_T=\{<M,w>|\text{M is the TM from T}\}$$
	1) If $w=s$ 
		- Simulate $M(<w>)$
		- If that simulation accepts, then accept $w$.
		- Else, reject $w$.
	2) Else if $w=s^R$
		- Accept $w$.
	3) Else $w\neq s$
		- Reject

3) Show correctness of the reduction.
	1) $M$ accepts $w$
	2) $M$ does not accept $w$

4) Deciding $A_{TM}$ from $D_T$
	1) Construct the description of $M_T$
	2) Run $D_T$ on $M_T$
	3) If $D_T$ accepts, accept
	4) Else, Reject

$\therefore$ Our assumption that $T$ is decidable leads to a decision procedure for $A_{TM}$, $T$ is undecidable.