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


---
# (15 Points) Chomsky Normal Form (CNF)
Convert the following grammar into Chomsky Normal Form. You must list all steps.

$S\rightarrow AB|aB|C|\lambda$
$A\rightarrow aA|a|B|\lambda$
$B\rightarrow bB|b|C|A$
$C\rightarrow AB|b|\lambda$


---
# (5 Points) S-Grammar
Find an s-grammar that generates all strings from the following language:
$$
\begin{equation}\tag{Q.3}
L=\{a^nb^n:n\geq2\}
\end{equation}
$$


---
# (10 Points) Ambiguity & Derivation Tree
Given the following grammar:

$S\rightarrow AB|C$
$A\rightarrow aAb|ab$
$B\rightarrow cBd|cd$
$C\rightarrow aCd|aDd$
$D\rightarrow bDc|bc$

1) Draw a derivation tree for the string `aabbccdd`
2) Prove if the above grammar is ambiguous or not.

---
# (10 Points) NPDA
Construct an NPDA, using a state diagram, that accepts the language:
$$
\begin{equation}\tag{Q.5}
L=\{w:n_a(w)<n_b(w)\} \text{ where } \Sigma=\{a,b,c\}
\end{equation}
$$
Please also specify your stack alphabet in $\Gamma$. Please also use the same notation that is used in class when labeling your transitions. If different notations are used, then no credit will be given for the question. This includes not receiving the serious attempt points. **If a state diagram is not used, then no credit will be given as well.**
