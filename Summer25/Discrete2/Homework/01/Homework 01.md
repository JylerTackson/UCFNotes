**Problem Set:** 1
**Class:** COT 4210

Student Name: David Jackson
**Student ID:** 5298477
**Student NID:** da668497

---

# 1. Proof By Induction:
**(15 points)** Show that the following statement holds true using induction. Please show your steps in order to receive potential full credit. Skipping any steps of how things were derived can lead to not receiving full credit. Your proof must reach the same conclusion based on the given closed form. *Hint: If you get stuck with factoring polynomials that aren't quadratic, consider polynomial division to assist with determining factors.*
$$
\begin{equation}\tag{Q.1}
S_n=\sum^n_{k=1}\frac{k+4}{k(k+1)(k+2)}=\frac{n(3n+7)}{2(n+1)(n+2)}
\end{equation}
$$

$$\mathbf{\text{Base Case: N = 1}}$$
$$
\begin{equation}\tag{L.B.C}
L.H.S = \sum_{k=1}^1\frac{k+4}{k(k+1)(k+2)}=\frac{1+4}{1(1+1)(1+2)}=\frac{5}{6}
\end{equation}
$$
$$
\begin{equation}\tag{R.B.C}
R.H.S = \frac{1(3(1)+7)}{2(1+1)(1+2)}=\frac{10}{12}=\frac{5}{6}
\end{equation}
$$
$$\therefore \text{Base Case stands}$$
$$\mathbf{\text{Inductive Step}}$$
For my **Inductive Hypothesis** I will assume that the formula holds holds for $n=m$:
$$
\begin{equation}\tag{I.H}
S_m=\sum^m_{k=1}\frac{k+4}{k(k+1)(k+2)}=\frac{m(3m+7)}{2(m+1)(m+2)}
\end{equation}
$$
For the **Inductive Step** I want to show that the formula holds for $n=m+1$:
$$
\begin{equation}\tag{I.S}
S_{m+1}=\sum^{m+1}_{k=1}\frac{k+4}{k(k+1)(k+2)}=\frac{(m+1)(3(m+1)+7)}{2(m+2)(m+3)}
\end{equation}
$$
Begin by simplifying the **LHS** of the equation:
$$
\begin{equation}\tag{I.S}
S_{m+1}=\sum^{m+1}_{k=1}\frac{k+4}{k(k+1)(k+2)}=S_m+\frac{(m+5)}{(m+1)(m+2)(m+3)}
\end{equation}
$$
$$
\begin{equation}
S_{m+1}=\frac{m(3m+7)}{2(m+1)(m+2)} + \frac{(m+5)}{(m+1)(m+2)(m+3)}
\end{equation}
$$
Find common Denominator:
$$
S_{m+1}=\frac{m(3m+7)(m+3)+2(m+5)}{2(m+1)(m+2)(m+3)}
$$
Expand Numerator:
$$
S_{m+1}=\frac{3m^3+16m^2+32m+10}{2(m+1)(m+2)(m+3)}

$$
With the provided hint in the problem statement I noticed that the numerator could be broken down by using synthetic polynomial division.
$$\begin{array}{r|rrrr}
-1 & 3 & 16 & 23 & 10 \\
   &   & -3 & -13 & -10 \\
\hline
   & 3 & 13 & 10 & 0 \\
\end{array}$$
This results in a finalized factored numerator of:
$$
S_{m+1}=\frac{(m+1)^2(3m+10)}{2(m+1)(m+2)(m+3)}

$$
Simplify the **RHS** of the equation:

$$
\begin{equation}\tag{I.S}
S_{m+1} = \frac{(m+1)(3(m+1)+7)}{2((m+1)+1)((m+1)+2)}=\frac{(m+1)(3(m+1)+7)}{2(m+2)(m+3)}
\end{equation}
$$
Expand the numerator:
$$
S_{m+1}=\frac{(m+1)(3(m+1)+7)}{2(m+2)(m+3)}
$$
I finalize the RHS by fully expanding the top of the equation:
$$
S_{m+1}=\frac{3m^2+13m+10}{2(m+2)(m+3)}
$$

Finally... the LHS can be reduced once more to remove a factor of $(m+1)$ from both the top and bottom. The numerator can be expanded with the remaining factor of $(m+1)$ to create:
$$
S_{m+1}=\frac{3m^2+13m+10}{2(m+2)(m+3)}
$$
Therefore we have shown that:
$$\text{For }S_{m+1}=LHS=RHS$$
$$
\begin{equation}\tag{A.1}
S_m+1 = \frac{3m^2+13m+10}{2(m+2)(m+3)}=\frac{3m^2+13m+10}{2(m+2)(m+3)}
\end{equation}
$$

---
# 2.  Set Construction
**(5 Points)** Given sets $\mathbf{A}$ and $\mathbf{B}$ where $\mathbf{A = \{2,3,5,7\}}$ and $\mathbf{B=\{2,4,5,8,9\}}$ and the universal set $\mathbf{U=\{0,1,2,3,4,5,6,7,8,8,10\}}$.
List each member in set $\mathbf{S}$ which is defined as 
$$
\begin{equation}\tag{Q.2}
\mathbf{S = \overline{\overline{A} \cap B}}
\end{equation}
$$
- $\mathbf{\overline{A}=\{0,1,4,6,8,9,10\}}$
- $\mathbf{\overline{A}\cap B=\{4,8,9\}}$
- $\mathbf{\overline{\overline{A}\cap B}=\{0,1,2,3,5,6,7,10\}}$
$$
\begin{equation}\tag{A.2}
\mathbf{S=\{0,1,2,3,5,6,7,10\}}
\end{equation}
$$
---
# 3. DFA Construction
**(10 points)** Given $\mathbf{\Sigma = \{a,b\}}$, construct a DFA that recognizes the following language $\mathbf{L_3}$.
**NOTE:** $n_a(w) \text{ and } n_b(w)$ means the total number of $\text{a's}$ and number of $\text{b's}$ in $w$ respectively. Example: If $w=abbaaba$, then $n_a(w)=4 \text{ and } n_b(w)=3$.
$$
\begin{equation}\tag{Q.3}
L_3=\{w:(n_a(w)mod3\leq n_b(w)mod3\}
\end{equation}
$$
To begin I will define the 5-tuple definition of DFA:
$$
\begin{equation}\tag{DFA}
DFA=\{Q_D,\Sigma_D,\delta_D,q_{0_D},F_D\}
\end{equation}
$$
The language defines a condition where there are only 3 possible values of:
- $n_a(w) mod 3 = \{0,1,2\}$
- $n_b(w) mod 3 = \{0,1,2\}$

We can represent each DFA state as a pair of $(i,j)$ where we will have 9 possible states:
1) $(0,0)$
2) $(0,1)$
3) $(0,2)$
4) $(1,0)$
5) $(1,1)$
6) $(1,2)$
7) $(2,0)$
8) $(2,1)$
9) $(2,2)$

The language states we can ONLY have a final state where:
- $n_a(w)mod3\leq n_b(w)mod3$
$\therefore$ the Final states are:
1) (0,0)
2) (0,1)
3) (0,2)
4) (1,1)
5) (1,2)
6) (2,2)

Using the above information it would result in the following:
![[Pasted image 20250530154802.png]]
Where:
- $n_a = n_i$
- $n_b = n_j$

The finalized $DFA$ is:
$$
\begin{equation}\tag{A.3}
DFA=\{(00,01,02,10,11,12,20,21,22),\Sigma , \delta_D, (00), (00,01,02,11,12,22)\}
\end{equation}
$$


---
# 4. DFA Construction
**(15 points)** In the C programming language, a value can be designated as a character type through a deceleration statement where the prefix starts with `char` and ends with the suffix `;`. Between the prefix and suffix is the name of the variable. Let $\mathbf{C}$ be the language of valid characters declaration statements. A member of $\mathbf{C}$ must start with `char` and end with `;`. The member must have at least 2 characters in its variable name and cannot contain the `;` character.
Draw a DFA that recognizes $C$.

To begin I will define the formal definition of a DFA:
$$
\begin{equation}\tag{DFA}
DFA = \{Q_D,\Sigma_D,\delta_D,q_{0_D},F_D\}
\end{equation}
$$
For this problem I need to define:
- $Q\Rightarrow$ Set of states that recognize $C$
- $\Sigma \Rightarrow$ Alphabet that recognize $C$
- $\delta \Rightarrow$ Transition functions that recognize $C$
- $q_{0}\Rightarrow$ Start state for the DFA that recognizes $C$
- $F \Rightarrow$ Final start for the DFA that recognizes $C$

To begin, the problem states: "A member of $C$ must start with `char` and end with `;`." This statement tells us that the **Final state** $(F)$ MUST occur when the string $(w)$ has an occurrence of the `;` symbol. If there is an occurrence of the `;` symbol before the end of the string then the string will be invalid.

For Example:

| Example  | Valid        |
| -------- | ------------ |
| char c;  | $\times$     |
| char cc; | $\checkmark$ |
| ca;      | $\times$     |
| char cc  | $\times$     |
The $DFA$ is easily described using a straight line of nodes that connect by describing:
1) The prefix char
2) Confirming the next 2 inputs are NOT `;`
3) Repeating until the `;` is found and transition to the final state;

The described $DFA$ can be visualized as the following:
![[Pasted image 20250530163451.png]]
Furthermore, the $DFA$ is described as:
$$
\begin{equation}\tag{A.4}
DFA = \{(q_0,q_1,q_2,q_3,q_4,q_5,q_6,q_7,q_8), \Sigma_D, \delta_D, q_0,(q_7)\}
\end{equation}
$$


---
# 5. Grammar Construction
**(5 points)** Given the following DFA $M$. Construct a grammar $G$ that generates all strings that the DFA should recognize. Assume that $\Sigma=\{0,1\}$.
![[2025-05-21-152054_239x164_scrot.png]]

$$\text{Did Not Finish}$$

---
# 6. Language Construction
**(5 points)** Describe the language $L$ based on the following grammar $G=(V,\Sigma,R,S)$:
- $V=\{S\}$
- $\Sigma=\{a\}$
- $R=aaaaaS \;|\; aa$
- $S=\{S\}$
Based on your answer, please include a description of what led you to the conclusion in order to receive potential full credit on this question. Any key factors missing could result in not receiving full credit.

To begin, I will define a language by saying that it is simply a subset of a star closure alphabet that follows a set of rules.
- $L=\Sigma^*$
	- $\Sigma^*=\text{ All strings obtained by concatenating all symbols in the alphabet.}$
		- INCLUDES $\lambda \text{ (empty string).}$

The grammar is defined as a mechanism used to describe the language that generates our string ($w$) from the alphabet $(\Sigma)$. The grammar defines our:
- $V$ - Variable $\Rightarrow \{S\}$ 
- $\Sigma$ - Alphabet $\Rightarrow \{a\}$
- $R$ - Rules $\Rightarrow \{aaaaaS \;|\; aa\}$
- $S$ - Starting Symbol

I will start by constructing some sample strings following the rules provided within the grammar:

| Iteration | String                                                                                                               | Result                                 |
| --------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| 0         | $S\rightarrow aa$                                                                                                    | $aa \Rightarrow a^2$                   |
| 1         | $S\rightarrow aaaaaS \rightarrow aaaaa(aa)$                                                                          | $aaaaaaa \Rightarrow a^{7}$            |
| 2         | $S\rightarrow aaaaaS \rightarrow aaaaa(aaaaaS) \rightarrow aaaaa(aaaaa(aa))$                                         | $aaaaaaaaaaaa \Rightarrow a^{12}$      |
| 3         | $S\rightarrow aaaaaS \rightarrow aaaaa(aaaaaS) \rightarrow aaaaa(aaaaa(aaaaaS)) \rightarrow aaaaa(aaaaa(aaaaa(aa)))$ | $aaaaaaaaaaaaaaaaa \Rightarrow a_{17}$ |


We can see the pattern will continue:

| Iteration | Result   |
| --------- | -------- |
| 0         | $a^2$    |
| 1         | $a^7$    |
| 2         | $a^{12}$ |
| 3         | $a^{17}$ |
| 4         | $a^{22}$ |
| 5         | $a^{27}$ |
Every step in the iteration you are adding 5 $a's$ starting with a base of 2 $a's$.
This results in the following language:
$$
\begin{equation}\tag{A.6}
L=\{a^n | n=5k+2, k\geq0\}
\end{equation}
$$
---
$$\mathbf{\text{This concludes problem set 1 for COT 4210}}$$