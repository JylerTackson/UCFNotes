

# Problem 3: Probability and Bayes Nets (30 pts)
A smart home system monitors three variables:
1) **M:** Motion detected $\{binary:yes/no\}$
2) **L:** Lights $\{binary:on/off\}$
3) **A:** Alarm $\{binary:yes/no\}$
The system works as follows: Motion can cause lights to turn on. Both motion and lights being on can trigger the alarm.
**Given probabilities:**
- $P(+m)=0.3$
- $P(+l|+m)=0.9$
- $P(+l|-m)=0.2$
- $P(+a|+m,+l)=0.8$
- $P(+a|+m,-l)=0.6$
- $P(+a|-m,+l)=0.1$
- $P(+a|-m,-l)=0.01$
The above notation must be read as:
$$
\tag{Notation}
\begin{matrix}
P(child|parent)
\\
P(child|P_1,...,P_n)
\end{matrix}
$$
---
### Answer
#### **Part A:** 
Draw the Bayesian Network for this scenario.
![[Pasted image 20250915213903.png]]

---
#### **Part B:** 
Calculate $P(+a)$
$$
ANSWER
$$
Using the [[Formulas#6. Extended Law of Total Probability|extended law of total probability]] we will sum over multiple intermediate events to find $P(+a)$

$$
\begin{align}
P(+a)=&\sum_{ml}P(+a|m,l)\;P(l|m)\;P(m)\\\\
+&P(+a\mid +m,+l)P(+l\mid +m)P(+m)=(0.8)\cdot(0.9)\cdot(0.3)=0.216\\
+&P(+a\mid -m,+l)P(+l\mid -m)P(-m)=(0.1)\cdot(0.2)\cdot(0)=0\\
+&P(+a\mid +m,-l)P(-l\mid +m)P(+m)=(0.6)\cdot(0)\cdot(0.3)=0\\
+&P(+a\mid -m,-l)P(-l\mid -m)P(-m)=(0.01)\cdot(0)\cdot(0)=0
\\
P(+a)=&\;(0.216)+(0)+(0)+(0)=0.216
\end{align}
$$

---









