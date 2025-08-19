David Jackson
- 5298477
Discrete 2 - COT4210
- Steinberg
---
# 1) TM - Accept Language
(15 points) Let $\Sigma = \{a,b,c\}$. Construct a Turing Machine (using a transition graph) that accepts the language:  
   $$
   L = \{\,ab^m c^n : 1 \le n \le 3 \text{ and } m > 0\}.
   $$  
   Write the sequence of moves done by your TM when the input tape is  
   $$w = \text{abbcaa}.$$  
   Is \(w\) accepted? Please use the single-derivation notation $(\vdash)$ when writing each step.
   
$$~~--------------------~~$$
$$\text{ANSWER}$$
   ![[1752257447104-a172b2e9-4996-432c-8ba9-6cc3b491bb23_1.jpg]]


| Notation | String                    | Node  |
| -------- | ------------------------- | ----- |
| $\vdash$ | **a** bbcaa               | $q_0$ |
| $\vdash$ | a **b** bcaa              | $q_1$ |
| $\vdash$ | ab **b** caa              | $q_2$ |
| $\vdash$ | abb **c** aa              | $q_2$ |
| $\vdash$ | abbc **a** a              | $q_3$ |
| $\vdash$ | abbca **a**               | $q_4$ |
| $\vdash$ | abbcaa $\mathbf{\square}$ | $q_5$ |
| $\vdash$ | abbca **a**               | $q_f$ |


---
# 2) TM - Reverse String
(10 points) Construct a Turing Machine (using a transition graph) to compute the function $f(s) = s^R$ where $s \in \{a,b\}^+$.  

Example: $s = abbaab$ would cause $f(s) = baabba$.  

**Input**: $w(s)$  
**Output**: $w(s^R)$  

**Computation**:  
$$
q_0\,w(s)\;⊢^*\;w(s^R)\;q_f
$$

$$~~--------------------~~$$
$$\text{ANSWER}$$
In this approach we will have two tapes:
- $T_1$ which will house the input string $w(s)$
- $T_2$ which we will write $w(s^R)$

![[yes (2)-1.png]]

In the above diagram we have 4 steps:
1) Iterate through Tape 1 until the pointer is at the first null space $(\square)$ in the string. Tape 2 is full of null spaces at this point so we can move left or right so I put stay $S$ for the time being.

2) At this point, Tape 1's pointer is at the first null space that occurs after the string so when we read that in we move it one back to the left moving it to the end of the string in Tape 1.

3) In $q_2$ we traverse through Tape 1 moving backwards through the input string. While we are traversing we write every a and b encountered to Tape 2 replacing the null spaces.

4) Once we traverse the entire string, Tape 1's pointer is at the first null space prior to the string and Tape 2's pointer is at the first null space after the reversed string. We move Tape 1's pointer forward 1 to be at the beginning of the string and move Tape 2's pointer backward 1 to be at the end of the reversed String.

Our output for Tape 2 is the reversed string in the form of $w(s^R)\;q_f$
Our output for Tape 1 is the original string in the form of $q_0\,w(s)$

---
# 3) TM - Unary Notation
(10 points) Construct a Turing Machine (using a transition graph) that computes the function $f(n) = n - 3$ if $n \ge 3$ and $f(n) = 0$ for $0 \le n < 3$. You may assume that the tape input is in unary notation.

$$
f(n) = \begin{cases}
n - 3, & n \ge 3,\\
0,     & 0 \le n < 3.
\end{cases}
$$

**Example 1:**  
$n = 5,\quad w(n) = 11111$  
**Input**: $w(n)$  
**Output**: $w(n - 3)$  

**Computation**:  
$$
q_0\,w(n)\;\vdash^*\;q_4\,w(n - 3)
$$

**Example 2:**  
$n = 2,\quad w(n) = 11$  
**Input**: $w(n)$  
**Output**: $w(0)$  

**Computation**:  
$$
q_0\,w(n)\;\vdash^*\;q_4\,w(0)
$$

$$~~--------------------~~$$
$$\text{ANSWER}$$

![[yes (1)-1.png]]


---
# 4) TM - List Languages
(5 points) A Turing Machine with “stay-put” instead of “left” is similar to the Standard Turing Machine, but its transition function has the form  
$$
\delta : Q \times \Gamma \to Q \times \Gamma \times \{R, S\}.
$$  
At each step, the machine can move its head right ($R$) or let it stay in the same position ($S$).

- **(a)** List the class of languages that these machines recognize.  
- **(b)** Based on your answer, does this Turing Machine have the same computational power as the Standard Turing Machine?

_Note: You only have to consider the languages we have covered in this course. Check the notes for guidance._  
$$~~--------------------~~$$
$$\text{ANSWER}$$
- **(a)** The class of languages that these machines recognize is:
  - Regular Languages
	  - It can only recognize regular languages due to several reasons\:
		  1) Since we cant move left we are effectively the same computation power as a DFA where we only get one pass through the input string.
		  2) We are still able to write to the tape however if we do we are unable to go back and see what has been written.
		  3) Staying at the same position provides minimal computation help as it is just reading and computing the same symbol before deciding to move forward.

- **(b)** This machine does **NOT** have the same power as the standard Turing Machine. Due to the reasons stated above, it is computationally comparable to a DFA.


---
# 5) TM -  Implementation‐level Description
(10 points) Give an implementation‐level description of the following Turing Machine that decides the following language over the alphabet $Σ = \{0,1\}$.

$$L = \{ w | \text{ w contains twice as many } 0\text{'s as }1's \}$$

_Note: You are not constructing a transition graph. Please only provide the implementation‐level description. If no implementation‐level description is provided, then no credit will be given in this question._
$$~~--------------------~~$$
$$\text{ANSWER}$$
To complete this question I am going to assume that the Language will only be accepted if it has **exactly** 2n as many 0's as 1's.

To begin, you will have three separate tapes:
- $\text{Tape }1 \; (T_1)$: This will be the initial input tape that contains the string $w$
- $\text{Tape }2 \; (T_2)$: This will be a tape that we use to count the amount of $0's$
- $\text{Tape }3 \; (T_3)$: This will be a tape that we use to count the amount of $1's$

1) Iterate through $T_1$, every time a 0 is encountered mark $T_2$ with an $X$ and move the pointer to the right; every time a 1 is encountered mark $T_3$ with a $Y$ and move the pointer to the right.
   
   After going through the entire $T_1$ you should have $T_2 \text{ \& } T_3$ completely filled up with the $X's \text{ \& } Y's$ corresponding to the number of 0's and 1's within $T_1$. Now loop the pointers in $T_1, T_2, T_3$ back to the beginning of the tape.

2) We will begin going through $T_2 \text{ \& }T_3$ pairing every Y in $T_3$ with two X's in $T_2$.
	- On $T_3$ replace the left-most $Y$ with a $Y^\prime$, leave the pointer on this cell
	- On $T_2$ replace the left most $X$ with an $X^\prime$
		- If none is found, **reject**
	- Move right to find the next left most $X$ and replace that with an $X^\prime$

3) Return both heads of $T_2 \text{ \& } T_3$ to the head of the tape and repeat step 2.
	- Once a loop finishes check if there are no more entries in $T_3$.
	  If there are still entries in $T_2$ but none left in $T_3$, **reject**

4) Accept: Every $Y (1)$ has been paired with 2 $X's(0)$.