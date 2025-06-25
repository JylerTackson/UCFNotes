

### Pigeon Hole Principle
- **Theorem:** If $k$ is a positive integer and $k+1$ objects are placed into $k$ boxes, then at least one box contains one two or more objects.
- **Proof:** Lets use a proof by contra position. Suppose none of the $k$ boxes has more than one object. Then the total number of objects would be at most $k$. This contradicts the statement that we have $k+1$ objects.

#### Pigeonholes & DFA's
- If you have $k+1$ symbols and $k$ states you can come to the conclusion that you must **revisit** a state at least once in order to have a valid $DFA$.
---
### Pumping Lemma  - Regular Expressions
If $A$ is a regular language, then there is a number $p$, the **pumping length**, s.t. if $s$ is a string in $A$ with length of at least $p$, then $s=xyz$ so that:
- $xy^iz$ is a string in $A$ for all $i\geq0$
- $|y|>0$
- $|xy|\leq p$
Notes:
- $x$ and $z$ can be empty, but $y$ CANNOT. This is the whole point of the lemma.
- We call it a lemma because all its good for it showing that some languages **aren't** regular.

### Pumping Lemma Proof:
##### Formal Proof
Let $M=(Q, \Sigma, \delta, q_0, F)$ be a DFA recognizing language A, and let $p= |Q|.$
- Consider $s\in A$ s.t. $|s|=n\text{, with }n\geq p$.
- Show that $s=xyz$ s.t. $sy^iz$ **is a string in $A \; \forall \; i\geq 0\text{, with } |y| > 0 \text{ and } |xy|\leq p$.**

##### Proof Ideas:
By combining the above ideas and the pigeon hole principle, we are trying to say:
- We can go around the cycle **as many times as we want**, since its a **cycle.**
- The before and after parts can be empty, but the cyclic part **cant be empty** or we don't have enough states.
- We have to hit some state twice by the time we hit a number of symbols **equal** to the number of states.

##### Using the pumping lemma:
1) Set up the Pump
	- Assume a language is regular
	- Observe that, therefore, by the pumping lemma, there is a $p$ so that any string $s$ in $A$, of length $p$ or greater, can be cut into $xyz$
2) Break the Pump
	- Find a string $s$ in it of length $p$ or greater, that **cant** be pumped
	- Demonstrate that no matter how you cut it into $xyz$ it cannot be pumped
3) Clean up the mess
	- Observe that since string $s$ in $A$, of length $p$ or greater, cant be pumped; and $A$ is regular; we have a contradiction with the pumping lemma
	- We can conclude **$A$ is not regular.**


##### Examples of Pumping Lemma:
1) Show that $L=\{a^nb^n|n>0\}$ is not regular
	1) Assume by contradiction that $L$ is regular
	2) Pumping Lemma states there exists $n>0$ 