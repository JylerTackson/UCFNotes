## Linear Grammar
A grammar produces **Regular languages** if it is:
- We can have one variable per production.
- You CANNOT mix left and right linear.
- **Right Linear**
	- A grammar is **right linear** if all rules/productions are of the form:
		- $A\rightarrow xB$
		- $A\rightarrow x$
- **Left Linear**
	- A grammar is **left linear** if all rules/productions are of the form:
		- $A\rightarrow Bx$
		- $A\rightarrow x$

**Example 1:**
The following grammar $G_1 = \{\{S\}, \{a,b\}, R,S\}$
- $G_1 = S\rightarrow abS | a$
-  $G_1$ is a **right-linear** grammar.
- Derivation:
	- $ababa: S\rightarrow abS \rightarrow ababS \rightarrow ababa$

**Example 2:**
The following grammar $G_2 = \{\{S,A,B\}, \{a,b\}, R, S\}$
- $S \rightarrow Aab$
  $A\rightarrow Aab | B$
  $B\rightarrow a$
- $G_2$ is a **left-linear** grammar.
- Derivation
	- $aabab: S\rightarrow Aab \rightarrow Aabab \rightarrow Babab \rightarrow aabab$

## Context-Free Grammar
A grammar is considered **context-free** if **ALL** the rules are in the form:
- $A\rightarrow x$ where $A\in V$ and $x\in (V\cup \Sigma)^*$


### Examples:
Write a context-free grammar for the following languages:
1) $L=\{a^n ww^R b^n : w\in\{a,b^*\}, n>0\}$
	- $S\rightarrow aSb | sAb$
	- $A\rightarrow aAa | bAb | \lambda$

2) $L=\{a^nb^n : n is odd\}$
	- $S\rightarrow aaSbb | aaAbb$
	- $A \rightarrow ab$

3) $L=\{a^nb^m : n\neq m\}$
	- $S\rightarrow  A|B$
	- $A\rightarrow a|aAb|aA$
	- $B\rightarrow b|aBb|Bb$

