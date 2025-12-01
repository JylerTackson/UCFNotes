### Problem 2.1
We consider $(\mathbb{R}\textbackslash\{-1\},\star)$, where
$$
\tag{2.134}
\begin{matrix}
a\star b :=ab+a+b, &&a,b\in\mathbb{R} \textbackslash \{-1\}
\end{matrix}
$$
1) Show that $(\mathbb{R}\textbackslash\{-1\},\star)$ is an Abelian group:
2) Solve
$$
3\star x \star x = 15
$$
in the Abelian group $(\mathbb{R}\textbackslash\{-1\},\star)$, where $\star$ is defined in $(2.134)$.



> [!Answer] Part 1
> To show that $(\mathbb{R}\textbackslash\{-1\},\star)$ is an Abelian group I will refer back to the definition of an Abelian group:
> > [!Definition] Abelian Group
> > Consider $G:=(\mathcal{G}, \otimes)$, where we have a set $\mathcal{G}$ and an operation $\otimes:\mathcal{G}\times\mathcal{G}\to\mathcal{G}$ defined on $\mathcal{G}$. $G$ is a group iff:
> > 1) Closure of $\mathcal{G}$ under $\otimes: \forall x,y \in \mathcal{G}:x\otimes y \in \mathcal{G}$
> > 2) Associativity: $\forall x,y,z \in \mathcal{G}: (x\otimes y) \otimes z = x\otimes (y\otimes z)$
> > 3) Neutral element: $\exists e \in \mathcal{G} \forall x \in \mathcal{G}: x\otimes e=x and e\otimes x=x$
> > 4) Inverse element: $\forall x \in \mathcal{G} \exists y \in \mathcal{G} : x\otimes y = e$ and $y\otimes x = e$, where $e$ is the **neutral element**. We often write $x^{-1}$ to denote the inverse element of $x$.
> > 5) **Abelian Group (Commutativity):** If additionally, $\forall x,y \in \mathcal{G}: x\otimes y=y\otimes x$, then $G=(\mathcal{G},\otimes)$ holds true, the group is additionally an Abelian Group.
> 
> Therefore, to show that $(\mathbb{R}\textbackslash\{-1\},\star)$ is an Abelian Group we must first show that it is a group and then show that it is an Abelian Group:
> 1) To show **closure** we must show that for all $x \& y$ within our set $\mathcal{G}$, after applying our operation $\otimes$, $x$ & $y$ must remain in our set $\mathcal{G}$ after the operation is performed.
> 	$$\begin{align}
> 	ab+a+b=&\;-1
> 	\\
> 	ab+a+b+1=&\;0
> 	\\
> 	(a+1)(b+1)=&\;0
> 	\end{align}$$
> We have closure because $a$ nor $b$ is allowed to be $-1$ by the assumption stated within the problem statement $\therefore a \star b$ is $\in \mathbb{R}\textbackslash\{-1\}$
> 
>2) To show **Associativity** we must show that the order of our operation performed on three separate variables  $x,y,z\in\mathcal{G}$ all have the same outcome.
>	$$
>	\begin{align}
>	x\otimes (y\otimes z)=&(x\otimes y)\otimes z
>	\\
>	
>	\end{align}
>	$$






