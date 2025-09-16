#### 1. Bayes' Definition

Used to define conditional probability: the probability of event $A$ occurring given that event $B$ has occurred. It forms the foundation for all conditional probability reasoning.

$$P(A∣B)= \frac{P(A,B)}{P(B)}$$

---

#### 2. Product Rule

Used to rewrite a joint probability $P(A,B)$ in terms of a marginal $P(B)$ and a conditional probability $P(A|B)$. Essential in probability chain rules and Bayesian networks.

$$P(A,B)=P(B)\,P(A \mid B)$$

---

#### 3. Symmetry of Intersection

States that the joint probability of two events is commutative—useful for simplifying or rearranging joint probabilities.

$$P(A,B)=P(B,A)$$

---

#### 4. Bayes' Theorem

Applies when you need to invert conditional probabilities: computing $P(A|B)$ when you know $P(B|A)$, $P(A)$, and $P(B)$. Widely used in Bayesian inference, classification, and updating beliefs.

$$P(A∣B)=\frac{P(B \mid A)\,P(A)}{P(B)}$$

---

#### 5. Law of Total Probability (Two Cases)

Decomposes the probability of $A$ into cases based on whether $B$ occurs or not. Used when partitioning the sample space into complementary events.

$$P(A)=P(A,B) + P(A,\neg B)$$

---

#### 6. Extended Law of Total Probability

A generalized version summing over multiple intermediate events $(b,c)$. Common in hierarchical or multi-step probability problems.

$$\sum_{b,c} P(A \mid b,c)\,P(c \mid b)\,P(b)$$

---

#### 7. Complement Rule for Conditionals

Used when it’s easier to calculate the complement of an event given $B$. Helps when directly computing $P(A|B)$ is difficult.

$$P(A∣B)=1 - P(\neg A \mid B)$$

---

#### 8. Partition Formula

Splits the conditional probability $P(A|B)$ across two mutually exclusive conditions ($c$ and $\neg c$). Helpful for breaking problems into simpler conditional components.

$$P(A∣B)=P(A \mid B,c)\,P(c \mid B) + P(A \mid B,\neg c)\,P(\neg c \mid B)$$

---

