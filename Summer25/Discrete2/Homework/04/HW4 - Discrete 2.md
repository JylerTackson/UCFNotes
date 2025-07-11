# 1) TM - Accept Language
(15 points) Let $\Sigma = \{a,b,c\}$. Construct a Turing Machine (using a transition graph) that accepts the language:  
   $$
   L = \{\,ab^m c^n : 1 \le n \le 3 \text{ and } m > 0\}.
   $$  
   Write the sequence of moves done by your TM when the input tape is  
   $$w = \text{abbcaa}.$$  
   Is \(w\) accepted? Please use the single-derivation notation $(\vdash)$ when writing each step.
   ![[1752257447104-a172b2e9-4996-432c-8ba9-6cc3b491bb23_1.jpg]]
   
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

---
# 5) TM -  Implementation‐level Description
(10 points) Give an implementation‐level description of the following Turing Machine that decides the following language over the alphabet $Σ = \{0,1\}$.

$$L = \{ w | \text{ w contains twice as many } 0\text{'s as }1's \}$$

_Note: You are not constructing a transition graph. Please only provide the implementation‐level description. If no implementation‐level description is provided, then no credit will be given in this question._
