# Write a CFG for the following Languages:
1) $L=\{a^nww^Rb^n:w\in\{a,b\}^*,n>0\}$
	- $S\rightarrow aSb | aAb$
	- $A\rightarrow aAa | bAb | \lambda$
		- Pronoun of $n$ number of $a's$
		- Suffix of $n$ number of $b's$
		- And string $w$ in the middle concatenated to itself $R$ times
			- where $w\in\{a,b\}^*$

2) $l=\{a^nb^n:\text{ n is even }\}$
	- $S\rightarrow aaSbb|\lambda$

3) $L=\{a^nb^n:\text{ n is odd }\}$
	- $S\rightarrow aAb$
	- $A\rightarrow aaAbb|\lambda$
		- The addition of the A non terminal makes it so you must add 1 to the start of the counting $\therefore$ you will always end up with an odd number of terminals with this langauge.

4) $L=\{a^nb^m:n\neq m\}$
	- $S\rightarrow S_1|S_2$
	- $S_1\rightarrow aS_1b|S_1b|b$
	- $S_2 \rightarrow aS_2b|aS_2|a$
		- Why this is correct:
			- If you have $S_1 \text{ \& } S_2$ ending in $\lambda$ it can result in $w=\lambda$ which indicates $n=m=0 \therefore$ you must have them ending in their respective terminal symbol $\{a,b\}$
			- Furthermore, allowing the non-terminals $\{S_1, S_2\}$ to call each other allow them to set the $a's$ and $b's$ equal to each other which we do not want.
			- This works by checking which is greater ($n \text{ or }m$) and going to its respective expression ($S_1 \text{ or }S_2$).

5) $L=\{a^nb^m:2n\leq m\leq3n \text{ and } n\geq 0, m\geq 0\}$
	- 