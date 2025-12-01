### Properties - Transpose & Inverse
$$
\begin{align}
\tag{2.26}
AA^{-1}=&\;I=A^{-1}A\\
\tag{2.27}
(AB)^{-1} =&\; B^{-1}A^{-1}\\
\tag{2.28}
(A+B)^{-1}\neq &\; A^{-1} + B^{-1}\\
\tag{2.29}
(A^\top)^\top = &\; A\\
\tag{2.30}
(AB)^\top = &\; A^\top B^\top\\
\tag{2.31}
(A+B)^\top =&\; A^\top + B^\top
\end{align}
$$

---
### Definition 2.7 - Group
Consider $G:=(\mathcal{G}, \otimes)$, where we have a set $\mathcal{G}$ and an operation $\otimes:\mathcal{G}\times\mathcal{G}\to\mathcal{G}$ defined on $\mathcal{G}$. $G$is a group iff:
1) **Closure** of $\mathcal{G}$ under $\otimes: \forall x,y \in \mathcal{G}:x\otimes y \in \mathcal{G}$
2) **Associativity**: $\forall x,y,z \in \mathcal{G}: (x\otimes y) \otimes z = x\otimes (y\otimes z)$
3) **Neutral** element: $\exists e \in \mathcal{G} \forall x \in \mathcal{G}: x\otimes e=x and e\otimes x=x$
4) **Inverse** element: $\forall x \in \mathcal{G} \exists y \in \mathcal{G} : x\otimes y = e$ and $y\otimes x = e$, where $e$ is the **neutral element**. We often write $x^{-1}$ to denote the inverse element of $x$.
5) **Abelian Group (Commutativity):** If additionally, $\forall x,y \in \mathcal{G}: x\otimes y=y\otimes x$, then $G=(\mathcal{G},\otimes)$ holds true, the group is additionally an Abelian Group.
Groups can be thought of like a set and a rule for combining these elements within the set. In the notation provided above, the set shown is $\mathcal{G}$ and the rule for combining these elements is notated as $\otimes$ and is further defined when needed.

---
### Definition 2.9 - Vector Space
A real-valued vector space $V=(V,+,\cdot)$ is a set $\mathcal{V}$ with two operations
$$
\begin{align}
\tag{2.62}
+:\mathcal{V}\times \mathcal{V} \to&\; \mathcal{V}\\
\tag{2.63}
\cdot : \mathbb{R} \times \mathcal{V} \to &\; \mathcal{V}
\end{align}
$$
where:
1) $(\mathcal{V}, +)$ is an abelian group.
2) Distributivity holds true
3) Associativity holds true
4) There exists a neutral element w.r.t to the outer operation

The dimension of a vector space corresponds to the number of its basis vectors.

---
### Definition 2.10 - Vector Subspace
Let $V=(\mathcal{V},+,\cdot)$ be a vector space and $\mathcal{U} \subseteq \mathcal{V}, \mathcal{U}\neq \emptyset$. Then $U = (\mathcal{U},+,\cdot)$ is called a vector subspace if $U$ is a vector space with the operations $+$ and $\cdot$ 

To determine whether $(\mathcal{V}, +, \cdot)$ is a subspace of $V$ we still need to show the following:
1) $\mathcal{U}\neq \emptyset$ in particular: $0\in \mathcal{U}$
2) Closure of $U$:
	1) w.r.t to the outer (Multiplication) and inner (addition) operation.

---
### Definition 2.14 - Basis & Rank
A basis is a minimal generating set and a maximal linearly independent set of vectors. The basis contains as many linearly independent vectors as possible and you are unable to add anymore without creating dependencies. The basis contains just enough vectors to space the space.

A basis of a subspace can be found by executing the following steps:
1) Write the spanning vectors as columns of a matrix
2) Determine the row-echelon form
3) The spanning vectors associated with the pivot columns are a basis of the vector space.

Just as Basis is the number of linearly independent columns, **Rank** is the number of linearly independent rows; denoted by $rk(A)$

### Properties - Rank
- $rk(A)=rk(A^\top)$

---
### Definition 2.15 - Linear Mapping
A linear mapping is a function between vector spaces that preserves:
1) Vector Addition: $T(u+v)=T(u)+T(v)$
2) Vector scalar multiplication: $T(cv)= cT(v)$
Linear mappings keep the structure of vector spaces intact, never bending, curving, or distorting the vector space allowing for the linearity to be preserved.

#### Special Cases: In|Sur|Bi - jective mappings
There are three special cases of linear mappings that we will introduce that also introduce special linear mappings:
1) Injective Mappings refer to a **One-to-One** mapping where every input results in a different output
2) Surjective Mappings refers to an **Onto** mapping where every vector in the target space is hit by at least one vector from the domain.
3) Bijective Mappings is a combination of both Injective and Surjective. This mapping creates a perfect correspondence between the two spaces and guarantees an inverse linear map exists.

#### Special Cases: Iso|Endo|Auto - morphism
There are several types of mappings that can be identified based upon the outcome of the linear mappings identified between the target and input vector spaces
1) Isomorphism: $\Phi: V\to W$ linear and bijective
2) Endomorphism: $\Phi: V\to V$ linear
3) Automorphism: $\Phi:V\to V$ linear and bijective
4) We define $id_V:V\to V$, $x\to x$ as the identity mapping or identity automorphism in $V$

##### Theorem 2.17
Finite-dimensional vector spaces are isomorphic iff $dim(V)=dim(W)$

---
### Definition 2.19 - Transformation Matrix
Consider vector spaces $V,W$ with corresponding bases $B,C$ 

---
### Theorem 2.20 - Basis Change
