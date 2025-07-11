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
		- The addition of the A non terminal makes it so you must add 1 to the start of the counting $\therefore$ you will always end up with an odd number of terminals with this language.

4) $L=\{a^nb^m:n\neq m\}$
	- $S\rightarrow S_1|S_2$
	- $S_1\rightarrow aS_1b|S_1b|b$
	- $S_2 \rightarrow aS_2b|aS_2|a$
		- Why this is correct:
			- If you have $S_1 \text{ \& } S_2$ ending in $\lambda$ it can result in $w=\lambda$ which indicates $n=m=0 \therefore$ you must have them ending in their respective terminal symbol $\{a,b\}$
			- Furthermore, allowing the non-terminals $\{S_1, S_2\}$ to call each other allow them to set the $a's$ and $b's$ equal to each other which we do not want.
			- This works by checking which is greater ($n \text{ or }m$) and going to its respective expression ($S_1 \text{ or }S_2$).

5) $L=\{a^nb^m:2n\leq m\leq3n \text{ and } n\geq 0, m\geq 0\}$
	- $S\rightarrow aSbb|aSbbb|\lambda$

6) $L=\{a^nb^m:n\leq m+3\}$
	- $S\rightarrow aSb|A$
	- $A\rightarrow Ab|a|aa|aaa|\lambda$
		- When solving this problem,  you should consider the base case:
			- $m=0 \text{ and } n=\{0,1,2,3\}$
		- This helps you construct from the beginning as all other cases build from this.

7) $L=\{a^nb^m:n=m-1\}$
	- $S\rightarrow aSb|b$
		- Taking into account the base case:
			- $n=0 \text{ and } m=1$
			- Would result in just a $b$

8) $L=\{a^nb^mc^l : n\geq0,m\geq0,l\geq0 : l=m+n\}$
	- $S\rightarrow aSc|A$
	- $A\rightarrow bAc|\lambda$
		- Taking into account the base case:
			1) $n=1 \;;\; m=1 \;;\; l=2$
			2) $n=0 \;;\; m=1 \;;\; l=1$
			3) $n=1 \;;\; m=0 \;;\; l=1$
			4) $n=0 \;;\; m=0 \;;\; l=0$


9) $L=\{a^nb^mc^l:n\geq0,m\geq0,l\geq0,n=m \;\text{ or }\; m\leq l\}$
	- ###### Tough
![[Pasted image 20250702172059.png]]
- When attempting this question you see that there are two base case(s) you must take into account:
	1) $n=m$
	2) $m\leq l$

10) $L=\{a^nb^mc^l : n\geq0, m\geq 0, l\geq0, l=2m+n\}$
	- $S\rightarrow aSc|A$
	- $A\rightarrow bAcc|\lambda$
		- Taking into account the base case:
			1) $n=1 \;;\; m=1 \;;\; l=3$
			2) $n=0 \;;\; m=1 \;;\; l=2$
			3) $n=1 \;;\; m=0 \;;\; l=1$
			4) $n=0 \;;\; m=0 \;;\; l=0$
		- You see that it is very similar to question 8, the only change is that with every $m$ there is 2 $l's$

---

11) Draw a Derivation Tree for the following sentence `abaabbaaba` derived from the following grammar:
$$\begin{equation}\tag{Q.11}
S\rightarrow aSa|bsb|\lambda
\end{equation}$$
![[Pasted image 20250702173551.png]]


12) Draw Derivation tree for the following sentence $aabbbb$ with the grammar:
$S\rightarrow AB|\lambda$
$A\rightarrow aB$
$B\rightarrow Sb$

![[Pasted image 20250702174553.png]]

---

13) Convert the following CFG into **Chomsky Normal Form (CNF):**

$S\rightarrow ASA|aB$
$A\rightarrow B|S$
$B\rightarrow b|\lambda$

1) Create a new start variable:

$S_0 \rightarrow S$
$S\rightarrow ASA|aB$
$A\rightarrow B|S$
$B\rightarrow b|\lambda$

2) Replace all $\lambda$ transitions:

To remove the $\lambda$ transitions we must forecast all the possible transitions that take into account the $\lambda$ operator and place those transitions in their rightful place:
- $S\rightarrow ASA|aB$ 
	- However when considering the lambda transition, both $A$ and $B$ can end up $\lambda \therefore$
		- $S\rightarrow ASA|aB|S|AS|SA|a$
	- Now we can safely remove the lambda transition from $B$

$S_0 \rightarrow S$
$S\rightarrow ASA|aB|a|AS|SA|S$
$A\rightarrow B|S$
$B\rightarrow b$

3) Replace Unit Tests:

- A unit test is a non-terminal that transitions into another single non-terminal; the unit tests we must take into account are:
	- $S_0\rightarrow S$
	- $S\rightarrow S$
	- $A\rightarrow B$
	- $A\rightarrow S$

	1) $S_0\rightarrow S$
		- Simply replace $S$ with what it can transition into resulting in:
			- $S_0\rightarrow ASA|aB|a|AS|SA|S$
	2) $S\rightarrow S$
		- You can simply replace this rule as it is redundant. It is stating that a state will transition into itself yet add nothing to the output of the grammar.
		- When performing the above step we also added a unit tests $S_0\rightarrow S$, the redundancy is there as well as it is allowing $S_0$ to transition into $S$ without contributing anything to the grammar.
	3) $A\rightarrow B \text{ and } A\rightarrow S$
		- As we did previously with $S_0 \rightarrow S$ we will simply replace these single state transitions with what the states are equal too:
			- $A\rightarrow b|ASA|aB|a|AS|SA$


4) Convert remaining rules into the proper form:
	- Proper form for a CNF grammar has 2 rules:
		1) Non-terminals can transition to 2 other non-terminals.
		2) Non-terminals can transition to a single terminal.
![[Pasted image 20250701203120.png]]

We have now transferred our grammar to the form:
- $S_0\rightarrow ASA|aB|a|AS|SA$
- $S \rightarrow ASA|aB|a|AS|SA$
- $A\rightarrow b|ASA|aB|a|AS|SA$
- $B\rightarrow b$
However this does not follow the 2 rules given for a CNF grammar.

I will fix this by defining 2 new states:
- $T\rightarrow AS$
- $X\rightarrow a$
We can substitute these states into our grammar by doing the following:

- $S_0\rightarrow TA|XB|a|AS|SA$
- $S \rightarrow TA|XB|a|AS|SA$
- $A\rightarrow b|TA|XB|a|AS|SA$
- $B\rightarrow b$
- $T\rightarrow AS$
- $X\rightarrow a$

Now we have satisfied all the rules for a Chomsky Normal Form Grammar.

14) Convert the following CFG into a CNF
	
	$S\rightarrow ABa|aB$
	$A\rightarrow aaB$
	$B\rightarrow Ac$
	
	1) Create a new start variable:
		- $S_0\rightarrow S$
		- $S\rightarrow ABa|aB$
		- $A\rightarrow aaB$
		- $B\rightarrow Ac$
	2) Remove $\lambda$ transitions:
		- There are no $\lambda$ transitions however to do this you would create all the needed transitions if a lambda did occur and put those in place.
	3) Remove Unit Tests:
		- $S_0\rightarrow S$
			- $S_0\rightarrow ABa|aB$
		However now state $S$ is unreachable so we can remove this state simply returning us to our prior Grammar
	4) Put in Proper Form
		- Put in proper form by adding new states to the grammar:
			1) $X\rightarrow a$
			2) $Y\rightarrow c$
			3) $Z\rightarrow b$
			4) $V\rightarrow XX$
			5) $W\rightarrow AB$
		- We can incorporate these by doing:
			- $S\rightarrow WX|XB$
			- $A\rightarrow VB$
			- $B\rightarrow AY$
			- $X\rightarrow a$
			- $Y\rightarrow c$
			- $Z\rightarrow b$
			- $W\rightarrow AB$
			- $V\rightarrow XX$
We now have a CNF grammar generated from the provided grammar.