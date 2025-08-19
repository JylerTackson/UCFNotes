### Question 1 - $HALT_{TM}$

Considering the following Turing Machine: 
$$HALT_{TM}=\{<M,w>|\text{M is a TM and M halts on input w}\}$$
Show that $HALT_{TM}$ is undecidable.
$$ANSWER$$

Take something that you know, for example, you know that acceptance TM is undecidable and perform reduction on this problem.

#### Proof by Contradiction
We are going to assume by way of contradiction that $HALT_{TM}$ is decidable, and build our machine to decide $A_{TM}$.



---
### Question 2 - $E_{TM}$

Consider the following Turing Machine:
$$E_{TM}=\{<M>|\text{M is a TM and L(M) = }\emptyset\}$$
Show that $E_{TM}$ is undecidable.
$$ANSWER$$

---
### Question 3 - $REGULAR_{TM}$

Consider the following Turing Machine:
$$REGULAR_{TM}=\{<M>|\text{M is a TM and L(M) is a regular language}\}$$
Show that $REGULAR_{TM}$ is undecidable.
$$ANSWER$$

---

### Question 4 - $EQ_{TM}$

Consider the following Turing Machine:
$$EQ_{TM}=\{<M_1,M_2> \; | \; M_1 \text{ and } M_2 \text{are TMs and }\;L(M_1)=L(M_2)\}$$
Show that $EQ_{TM}$ is undecidable.
$$ANSWER$$

---
### Question 5
Consider the problem of determining whether a two-tape Turing machine ever writes a nonblank symbol on its second tape when it is run on input $w$. Formulate this problem as a language and show that it is undecidable.
$$ANSWER$$

---
### Question 6
Consider the problem of determining whether a two-tape Turing machine ever writes a nonblank symbol on its second tape during the course of its computation on any input string. Formulate this problem as a language and show that it is undecidable.
$$ANSWER$$
