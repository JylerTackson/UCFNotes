# Homework 3
David Jackson
- 5298477
Discrete 2 - COT4210
- Steinberg
---
# (10 Points) Context Free Grammar (CFG)
Construct a CFG for the following language:
$$
\begin{equation}\tag{Q.1}
L=\{a^nb^mc^k:n\geq0,m\geq0,k\geq0,k=|n-m|\}
\end{equation}
$$

$S\rightarrow A|UB$
$U\rightarrow aUb|\lambda$
$A\rightarrow aAc|U$
$B\rightarrow bBc|\lambda$

---
# (15 Points) Chomsky Normal Form (CNF)
Convert the following grammar into Chomsky Normal Form. You must list all steps.

$S\rightarrow AB|aB|C|\lambda$
$A\rightarrow aA|a|B|\lambda$
$B\rightarrow bB|b|C|A$
$C\rightarrow AB|b|\lambda$

1) Create a new start state:

$S_0\rightarrow S$
$S\rightarrow AB|aB|C|\lambda$
$A\rightarrow aA|a|B|\lambda$
$B\rightarrow bB|b|C|A$
$C\rightarrow AB|b|\lambda$

2) Remove rewrites to $\lambda$:

$S_0\rightarrow S$
$S\rightarrow AB|B|A|aB|C|a$
$A\rightarrow aA|a|B$
$B\rightarrow bB|b|C|A$
$C\rightarrow AB|A|B|b$

Now all $\lambda$ transitions have been removed and the states have been updated

3) Get rid of unit rules:
	If you proceed by just replacing a unit Production with its ruleset you will simply loop and never achieve your desired output. Therefore I am doing this by replacing all Unit Productions with its non-Unit Productions:
	1) Gather Unit Productions:
		- $S_0\rightarrow \{S\}$
		- $S\rightarrow \{A,B,C\}$
		- $A\rightarrow \{B\}$
		- $B\rightarrow \{A,C\}$
		- $C\rightarrow \{A,B\}$
	2) Gather Non-Unit Productions:
		- $S\rightarrow {}$
		- $S \rightarrow \{AB,aB,a\}$
		- $A\rightarrow \{aA,a\}$
		- $B\rightarrow \{bB,b\}$
		- $C\rightarrow \{AB,b\}$
	3) Replace all Unit Productions with there corresponding Non-Unit Productions (Removing Duplicates).
		- $S_0\rightarrow AB|bB|b|aA|aB|a$
		- $S\rightarrow AB|bB|b|aA|aB|a$
		- $A\rightarrow aA|a|bB|b$
		- $B\rightarrow bB|b|AB|aA|a$
		- $C\rightarrow AB|aA|a|bB|b$
			- **NOTE:** Since rule $S$ is now unreachable, we can just remove the new start state we created and keep $S$ as our start state.
This results in the Grammar:

- $S\rightarrow AB|bB|b|aA|aB|a$
- $A\rightarrow aA|a|bB|b$
- $B\rightarrow bB|b|AB|aA|a$
- $C\rightarrow AB|aA|a|bB|b$

4) Convert all the remaining rules:
Finally, we must convert the remaining rules to follow the CNF rule:
- I will begin by adding extra states:
	- $X\rightarrow a$
	- $Y\rightarrow b$
- This brings me to:
	- $S\rightarrow AB|YB|b|XA|XB|a$
	- $A\rightarrow XA|a|YB|b$
	- $B\rightarrow YB|b|AB|XA|a$
	- $C\rightarrow AB|XA|a|YB|b$
	- $X\rightarrow a$
	- $Y\rightarrow b$
I have now transferred the given grammar to a CNF grammar.

---
# (5 Points) S-Grammar
Find an s-grammar that generates all strings from the following language:
$$
\begin{equation}\tag{Q.3}
L=\{a^nb^n:n\geq2\}
\end{equation}
$$
![[Pasted image 20250702222008.png]]





---
# (10 Points) Ambiguity & Derivation Tree
Given the following grammar:

$S\rightarrow AB|C$
$A\rightarrow aAb|ab$
$B\rightarrow cBd|cd$
$C\rightarrow aCd|aDd$
$D\rightarrow bDc|bc$

1) Draw a derivation tree for the string `aabbccdd`
![[CS Assignments - Frame 3 (1).jpg]]
2) Prove if the above grammar is ambiguous or not.
The above language is ambiguous, shown below is another example creating the string `aabbccdd` however using a different method but in the same grammar. This proves that it is an ambiguous grammar.

![[CS Assignments - Frame 4.jpg]]

---

# (10 Points) NPDA
Construct an NPDA, using a state diagram, that accepts the language:
$$
\begin{equation}\tag{Q.5}
L=\{w:n_a(w)<n_b(w)\} \text{ where } \Sigma=\{a,b,c\}
\end{equation}
$$
Please also specify your stack alphabet in $\Gamma$. Please also use the same notation that is used in class when labeling your transitions. If different notations are used, then no credit will be given for the question. This includes not receiving the serious attempt points. **If a state diagram is not used, then no credit will be given as well.**
