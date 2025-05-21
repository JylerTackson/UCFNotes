# 1. Proof By Induction:
**(15 points)** Show that the following statement holds true using induction. Please show your steps in order to receive potential full credit. Skipping any steps of how things were derived can lead to not receiving full credit. Your proof must reach the same conclusion based on the given closed form. *Hint: If you get stuck with factoring polynomials that aren't quadratic, consider polynomial division to assist with determining factors.*
$$
\begin{equation}\tag{Q.1}
S_n=\sum^n_{k=1}\frac{k+4}{k(k+1)(k+2)}=\frac{n(3n+7)}{2(n+1)(n+2)}
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
- $\mathbf{\overline{A}=\{1,4,6,8,9,10\}}$
- $\mathbf{\overline{A}\cup B=\{1,6,10\}}$
- $\mathbf{\overline{\overline{A}\cup B}=\{2,3,4,5,7,8,9\}}$
$$
\begin{equation}\tag{A.2}
\mathbf{S=\{2,3,4,5,7,8,9\}}
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


---
# 4. DFA Construction
**(15 points)** In the C programming language, a value can be designated as a character type through a deceleration statement where the prefix starts with `char` and ends with the suffix `;`. Between the prefix and suffix is the name of the variable. Let $\mathbf{C}$ be the language of valid characters declaration statements. A member of $\mathbf{C}$ must start with `char` and end with `;`. The member must have at least 2 characters in its variable name and cannot contain the `;` character.
Draw a DFA that recognizes $C$.

---
# 5. Grammar Construction
**(5 points)** Given the following DFA $M$. Construct a grammar $G$ that generates all strings that the DFA should recognize. Assume that $\Sigma=\{0,1\}$.
![[2025-05-21-152054_239x164_scrot.png]]


---
# 6. Language Construction
**(5 points)** Describe the language $L$ based on the following grammar $G=(V,\Sigma,R,S)$:
- $V=\{S\}$
- $\Sigma=\{a\}$
- $R=aaaaaS \;|\; aa$
- $S=\{S\}$
Based on your answer, please include a description of what led you to the conclusion in order to receive potential full credit on this question. Any key factors missing could result in not receiving full credit.