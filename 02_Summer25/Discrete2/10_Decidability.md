
# Regular Languages

## Decidability
Consider a language encoding the question of whether a given DFA accepts a given string.
$$A_{DFA}=\{<D,s>\;|\;\text{D is a DFA that accepts s}\}$$
Observe that:
- DFAs always finish computing in $|s|$ steps, with s being the input.
- A DFAs computational method is an [[09_Algorithm]].
- When passing the DFA and its string into the TM it is encoded, we can assume that the Church-Turing theorem has taken care of this step for us.

On input $<D,s>$
1) Simulate $D=(Q_D,\Sigma_D,\delta_D,q_{0D},F_D)$ on input s
2) The simulation follows the rule of a DFA.

Conclusion:
- Determining whether a DFA accepts a string is Turing-decidable (and hence, so is determining whether any regular language contains any string).

## Emptiness
Its useful to be able to figure out if a regular language is empty.
$$E_{DFA}=\{<D>\;|\;D\text{ is a DFA and L(D) = }\emptyset\}$$
Observe that:
- Any regular language can be recognized by a DFA
- A DFA accepts some string iff it's possible to get to an accept state from the start state.

On input $<D>$:
1) Mark the state of D.
2) Repeat until we don't mark any new states:
	1) Iterate through all marked states. For each state q:
		1) Mark all states that we can transition to from q.
3) If an accept state is marked, reject. Otherwise, accept.

Conclusion:
- Whether or not a regular language is empty is decidable.

## Equivalences
Its useful to be able to figure out whether two regular languages are equivalent.
$$EQ_{DFA}=\{<D,E>\;|\;\text{D and E are DFAs and L(D) = D(E)}\}$$
Recall the **symmetric difference $(A\; \triangle \;B)$:**
- $(A\; \triangle \;B)=(A-B)\cup(B-A)$
This will show equality because after doing this set operation the only thing remaining in both sets will be the empty set.

On input $<D_A,D_B>$
1) Construct $D_C$, a DFA that recognizes the symmetric difference of the two languages.
2) Determine if $L(D_C)$ is empty. Accept if so, else, reject.

## Example
Show that $A_{NFA}$ is a decidable language.
$$A_{NFA}=\{<B,s>\;|\; B\text{ is an NFA that accepts input string s}\}$$
Recall:
- Every NFA has an equivalent DFA

On Input $<B,s>$:
1) Convert NFA to its equivalent DFA $(C)$ using the procedure taught in class.
2) Simulate $C=\{Q_C,\Sigma_C,\delta_C,q_{0C},F_C\}$ on input $S$.
3) If the simulation ends on an acceptance state, accept, otherwise, reject.

### Alternative Solution:
Using a working TM from $A_{DFA}$ problem C slide notes
- $TM_{A}$
	- Name of TM used to decide $A_{DFA}$

Design a TM $(M)$, that decides $A_{NFA}$.

$M=$ on input $<B,s>$
1) Convert NFA B into its equivalent DFA C using the procedure from class.
2) Run $TM_A$ with $<C,s>$
3) If $TM_A$ accepts, accept, otherwise reject.


---

# Context Free Languages
The easy way to **recognizability** is to take a CFG and just keep iterating on it until you find a derivation that generates S; however, we want decidability NOT recognizability.

## Decidability
Think about a new grammar $G$ in Chomsky Normal Form. Every rule in a CNF grammar has one of the two forms:
- $A\rightarrow BC$
- $A\rightarrow a$

Observations:
1) Given s with $|s|=n$ there are exactly $2n-1$ steps to derive $s$:
	1) $n-1$ to grow out to $n$ variables
	2) $n$ to convert them all to terminals
2) There are a finite number of derivations with $2n-1$ steps in any CFG.

On input $<G,s>\text{, with } |s|=n$:
1) Find $n=|s|$
2) Convert G to CNF
3) Iterate through all derivations in G with $2n-1$ steps.
4) Otherwise reject.

## Emptiness
This is relatively the same for regular languages.

On input $<G>$:
1) Mark all the terminal symbols in $G$.
2) Repeat until no new variables get marked:
	1) Iterate over every rule $A\rightarrow R:$
		1) If every symbol in R has been marked, mark A.
3) If the start variable is marked, reject; otherwise, accept.

## Equivalence
Unlike Regular Languages, this is not decidable - CFL's aren't closed under complement or intersection.
![[Pasted image 20250721171457.png]]

---

# Undecidable

$A_{TM}$ is undecidable. Lets create a Turing Machine $U$ that recognizes $A_{TM}$

On input $<M,s>$
1) Simulate M on input s.
2) If M ever enters its accept state, accept. If M ever enters its reject state, reject.

This machine loops on input $<M,s>$ if M loops on s, which is why the machine does not decide $A_{TM}$.
If there was some magical way to determine $M$ was not halting on s, it could reject, but that doesn't exists!!!

### Some Observations:
Countability of Turing Machines
- For any given alphabet we can do the same thing to it that we did to the rational numbers
- In other words, the set of all strings over a given alphabet is countable.
- Any Turing machine $M$ can be encoded.
- **$\therefore$ the set of all Turing machines on a given alphabet is countable.**

Infinite Binary Sequences
- An infinite binary sequence is an unending sequence of 0s and 1s
- The set $B$ of all of them is uncountable for the same reason the real numbers are.

Languages and Infinite Binary Sequences
- Consider the set of all languages over a given alphabet
- Remember that each string over that same alphabet can be a number.
- Consider a characteristic sequence of binary digits representing a language: the $nth$ digit of this sequence is 1 iff the $nth$ string is in the language.
- That's a correspondence between the languages over any alphabet and $B$
- **The set of languages over a given alphabet is uncountable.**

---

# An Unrecognizable Language
Call a language co-Turing recognizable if its complement is recognizable.
- A language that is decidable is obviously both Turing recognizable and co-Turing recognizable.
- A language that's both Turing recognizable and co-Turing recognizable is almost as obviously decidable - just run the recognizer and co-recognizer in parallel, and return according to whichever one accepts first.
So a language is decidable iff it is both recognizable and co-recognizable.
$A_{TM}$ is obviously recognizable - but we've already proven that its undecidable. So $A_{TM}$ is unrecognizable.

#### Acceptance Turing Machine Problem
Consider the following Turing Machine:
$$A_{TM}=\{<M,s>|\text{M is a Turing machine that accepts s}\}$$
##### Proof By Contradiction
By way of contradiction, show that this machine is undecidable:
1) Assume its decidable.
	- Given that, there exists a decider $H$ for $A_{TM}$$$H(<M,s>)\text{ accepts if M accepts s and rejects otherwise}$$
2) Now consider a new machine called the "Devils Advocate" called $(D)$.
	- Takes a Decider as input and returns the opposite result.
3) You must consider all the possible machines that this can run therefore, you must consider:
	- $D(<D>)$
		- This is an obvious contradiction. $A_{TM}$ is undecidable.
![[Pasted image 20250723223840.png]]
---
## Examples

### Decidable using Graph
Let $\text{TRIANGLE}_G=\{<G>|G\text{ is a graph that contains a triangle}\}$
- Show that $\text{TRIANGLE}_G$ is decidable
![[Pasted image 20250723142133.png]]

You are going to create a Turing Machine that will run this graph:

- Remember what a graph is; a set of
	- Vertices
	- Edges

$M_{\text{TRIANGLE}}$: On input $<G>$, execute:
1) Obtain the following vertices V & edges E of G
2) For every distinct triplet of nodes (x, y, z) in the set of V
	1) If (x, y), (x, z), (y, z) - (assuming this is undirected) - $\in V$ then accept
3) If we haven't accepted, reject

--------------------
### Decidable using Regex
$\text{A}_\text{REX} = \{<R,s> | R \text{ is a regular expression that generates s}\}$
- Show that $A_\text{REX}$ is decidable.

You are going to create a Turing Machine that will run this REGEX:
$M_\text{REX}$: on input $<R,s>$

1) Convert REGEX $R$ into an $NFA$ ($A$) using $REGEX \to NFA$ procedure.
2) Run $TM_{A_{NFA}}$ (Can be found at the top of the notes) with input of $<A,s>$
	- We are feeding our NFA we created using our REGEX into our previously created TM that shows that a NFA is a decidable language.
3) If $TM_{A_{NFA}}$ Accepts, then we accept, else we reject.