Reduction is a way to turn one problem into another problem:
- Given the solution to problem **B**, solve problem **A**.

Reduction is important to decidability and recognizability because of the following observation:

---
### The Halting Problem
Let $HALT_{TM}=\{<M,s>|\text{ M is a Turing Machine that halts on input s}\}$

Assume BWOC that $TM$ $M_{HALT}$ decides $HALT_{TM}$. Construct the following machine $M_A$ to decide $A_{TM}$ for machine $M$ and input $s$:

$M_{A}$: On input $<M,s>$:

1) Run $M_{HALT}$ on $<M,s>$ to determine whether 
2) If $M_{HALT}$ rejects, then $M$ will not halt on s, and hence s is not in $L(M)$. Reject.
3) If $M_{HALT}$ accepts, then we can simulate $M$ on $s$ until it halts. Do so.
4) Reject or accept as does M.

This machine easily decides $A_{TM}$; but $A_{TM}$ is proven undecidable.
$\therefore$ $HALT_{TM}$ is undecidable.

---
### Emptiness of Turing machines
Let $E_{TM}=\{<M,s>|\text{ M is a Turing machine and L(M) }=\;\emptyset\}$

##### Inline Turing Machine Proof
- A Turing Machine can build another Turing Machine. (**Compiler**)
- Once we build this Turing machine, we then exploit its properties to prove that $E_{TM}$ is undecidable.
##### Example:
Assume BWOC that TM $M_{E}$ decides $E_{TM}$. Construct the following machine $M_A$ to decide $A_{TM}$ for machine $M$ and input $s$:

$M_A:$ On input $<M,s>$
- Build a new machine $M_1$
	- $M_1:$ on input $x$:
		- Reject if $x\neq s$
		- Otherwise, simulate $M$ on $s$, and accept or reject as it does.
- Run $M_E$ on $M_1$
- Accept if $M_E$ rejects; reject if $M_E$ accepts. 

###### Its important to keep track of all the players in the program:
- $E_{TM}$: is the language we are trying to prove is undecidable in the first place.
- $M_E$: is the machine that we assume exists to decide it, BWOC. **(Decider)**
- $M_A$: is the machine that we create to decide $A_{TM}$, proving the contradiction.
- $A_{TM}$: is the general acceptance problem for Turing machines, which we know is undecidable through the proof with the devil machine.
- $M_1$: is the machine that $M_A$ creates the process of its execution, that exploits the properties of $E_{TM}$ to make $A_{TM}$ decidable by way of $M_E$.

---
### Regularity of Turing Machines
Let $REGULAR_{TM}=\{<M,s>|\text{ M is a Turing Machine and L(M) is regular}\}$

Assume BWOC that TM $M_{REG}$ decides $REGULAR_{TM}$. Construct the following machine $M_{A}$ to decide $A_{TM}$ for machine $M$ and input s:

$M_A:$ On input $<M,s>$:

1) Build a new machine $M_1$:
	- $M_1$: On input $<x>$:
		1) Accept if $x$ has an irregular form
		2) Otherwise, simulate $M$ on $s$, and accept or reject as it does.\]
2) Run $M_{REG}$ on $M_1$
3) Accept if $M_{REG}$ accepts; reject if $M_{REG}$ rejects.

Once we run the decider on the Inline TM $(M_1)$ that will cause a contradiction.

---
### Equivalence of Turing Machines

Let $EQ_{TM}=\{<M_X,M_Y>| M_X\text{ and }M_Y\text{ are Turing Machines with }L(M_X)=L(M_Y)\}$ 

Assume BWOC that TM $M_{EQ}$ decides $E_{TM}$. Construct the following machine $M_E$ to decide $E_{TM}$ for machine $M$ and input $s$:

$M_E:$ On input $<M,s>$:
1) Build a new machine $M_1$:
	- $M_1$: On input $<x>$:
		1) Reject
2) Run $M_{EQ}$ on $<M,M_1>$
3) Accept if $M_{EQ}$ accepts; reject if $M_{EQ}$ rejects.

Once we run the decider with the inline TM ($M_1$) and the input machine $M$ we see a contradiction

NOTE:
- Its important to note that this machine is **RECOGNIZABLE** but what we are probing is that it is **UNDECIDABLE.**

---
### Computation History
A sequence of configurations of a TM $(M)$ on a given input $s$:
$$C_1,C_2, C_3, ...,C_f$$
s.t:
- $C_1$ is the start configuration of $M$ on s.
- $C_i$ transitions legally to $C_{i+1}$ for all relevant $i$.
- $C_F$ is a halting configuration $(\text{Either }q_{accept} \text{ or } q_{final})$.

Computation histories are finite sequences $\therefore$ if $M$ does not halt on $s$ there is no computation history for $M$ on $s$.

---
### Linear Bounded Automata
- A type of TM that cant move its head off the input to the right.

Given an $LBA$ with $q$ states, $g$ symbols in the tape alphabet and an input of length $n$, then there are a maximum of $qng^n$ configurations of that $LBA$.
- This means that $A_{LBA}$ is a decidable language
	- Run $LBA$ for $qng^n$ steps.
	- If it accepts,  accept. If it rejects, reject.
	- If it hasn't either accepted or rejected, then by the pigeonhole principle, it's repeated a configuration. We can observe with a bit of thought that:
		- **A TM that repeats a configuration can never halt.**
	- $\therefore$ if it hasnt accepted after $qng^n$ steps, reject.

$LBA's$ are good for:
- $CFL's$
- Regular Langauges

$LBA's$ are also very theoretically decidable.

### Undecidability of LBA's
Prove that $E_{LBA}$ is undecidable by a reduction from $A_{TM}$.
- This time we will be using the Computation History of the Turing Machine $M$ on input $s$.

Consider the construction of an $LBA$ $B(M,s)$ that accepts accepting computation histories for $M$ on input $s$. $B$ does the following:
1) Takes the Computation History as input:
2) Verifies that $C_1$ is the start configuration of $M$ on $s$.
3) Verifies that $C_{i+1}$ follows from its preceding $C_i$.
4) Verifies that $C_F$ is an accepting configuration for $M$.
---
![[Pasted image 20250726150606.png]]

---
### Post Correspondence Problem
We have a collection of dominoes, contains strings on the top and bottom:
$$\begin{equation}\tag{EX}
\left[\frac{a}{ab}\right]
\end{equation}$$
$$\begin{equation}\tag{Set of Dominoes}
\left[
\left[\frac{b}{ca}\right],
\left[\frac{a}{ab}\right],
\left[\frac{ca}{a}\right],
\left[\frac{abc}{c}\right]
\right]
\end{equation}$$
The goal is to make a list (repetitions allowed) s.t. the string from the top of the dominoes matches the string on the bottom.

Pulling from the set, we will now create a `Top String` and a `Bottom String` from the provided set of dominoes s.t. they match:

$$\begin{equation}\tag{Set of Dominoes}
\left[
\left[\frac{a}{ab}\right],
\left[\frac{b}{ca}\right],
\left[\frac{ca}{a}\right],
\left[\frac{a}{ab}\right],
\left[\frac{abc}{c}\right]
\right]
\end{equation}$$
When we evaluate the `Top String` and the `Bottom String` we see:
- Top String:
	- abcaaabc
- Bottom String:
	- abcaaabc

This is the Post Correspondence Problem

### Undecidability of PCP:
An instance of $PCP$ is a collection of Dominoes called $P$.
$$P=\left[
\left[\frac{t_1}{b_1}\right],
\left[\frac{t_2}{b_2}\right],\;
...\;,
\left[\frac{t_k}{b_k}\right]
\right]$$
and a match is a sequence $i_1, i_2, ... , i_l$  where:  $t_{i_{1}} \; t_{i_{2}} \; ... \; t_{i_{l}} = b_{i_{1}} \; b_{i_{2}} \; ... \; b_{i_{l}}$
$$PCP=\{<P> | \text{ P is an instance of the Post Correspondance Problem with a match}\}$$
Prove that $PCP$ is undecidable by using reduction through the computation history.
- We need to construct $P$ so that a match is an accepting computation history for $M$ on input $w$.
- Choose the collection of dominoes in $P$ so that making a match with **force** a simulation on $M$.
- 3 Technical points to consider about $M$:
	1) Assume $M$ on $w$ never attempts to move its head off the left -hand of the tape.
	2) If $w=\lambda$, use $\square$ in place of $w$.
	3) We require that a match starts with the $1^\text{st}$ domino
		- This last point changes the problem slightly now giving us the **Modified** Post Correspondence Problem (MPCP).

$$MPCP=\{<P> | \text{ P is an instance of the Post Correspondance Problem with a match that starts with the first domino}\}$$
$$PROOF$$
Let Turing Machine $R$ decide the $PCP$ and construct $s$ to decide $A_{TM}$.

1) Define Turing Machine $M$ which we need to simluate.
$$M=(Q,\Sigma,\Gamma,\delta,q_0,q_{accept}, q_{reject})$$
This construction has 7 parts which will all together accomplish simulating $M$ on $w$

- **(Part 1)**:
	-  
- 