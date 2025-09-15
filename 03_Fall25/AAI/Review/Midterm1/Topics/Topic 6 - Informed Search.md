In **Uninformed Search** you are only checking if you have or have not reached the goal, binary function $G(\cdot)$. However, in **Informed Search** consists of **integrating additional information about the goal** into our search for a plan.


### Heuristics
Formally defined as a **strategy or guideline** that helps you make progress toward a solution quickly, even if it doesn’t guarantee the _best_ or _perfect_ answer. A Heuristic is a function $h(s)\to \mathbb{R}$ that **estimates distance** between **a state and the goal**.
We can assume if:
- $G(s)=true$ then $h(s)=0$

---
### Greedy Search (a.k.a Best-first Search)
**Strategy:** Expand the node with the **lowest [[#Heuristics|heuristic]] value**.
- **Fringe:** **Priority queue** ordered by **smallest** $\mathbf{h(n)}$
	- $h(n)=$ [[#Heuristics|Heuristic]] of the state marking the node.
- **Quality:** Depends on the [[#Heuristics|heuristics]]
	- If [[#Heuristics|heuristics]] gets the **ordering correct** - you go straight to the solution

**Properties:**
- **[[#**Optimal **|Optimal:]]** NO
	- [[#Heuristics|Heuristics]] might lead you on a non-optimal path or goal.
- **[[#**Spatial/Space Complexity**|Space]] & Time Complexity:** Range Between ($BFS\Longleftrightarrow DFS$)
	- If the [[#Heuristics|heuristic]] is good, it can be any
	- If the [[#Heuristics|heuristic]] is bad, closer to DFS or worse
		- *Insight*: DFS and BFS are [[#Heuristics|heuristic]] search with particular [[#Heuristics|heuristic's]]
- **[[#**Complete **|Complete:]]** NO
	- If you are following the standard tree search algorithm, you will not get stuck, however; you can end up endlessly deep like in a DFS.

---
### A* Search
A **combination** between **[[Topic 5 - Uninformed Search#Uniform cost search (UCS)|Uniform Cost Search]] and [[#Greedy Search (a.k.a Best-first Search)|Greedy Search]]** 
$$
\begin{matrix}
\begin{matrix}
\begin{matrix}
\text{Uniform cost orders by path cost: }g(n)
\\
\text{Backward Cost}
\end{matrix}
&
\begin{matrix}
\text{Greedy orders by estimated goal proximity: }h(n)
\\
\text{Forward Cost}
\end{matrix}
\end{matrix}
\\\\
\text{A* orders by sum }f(n)=g(n)+h(n)
\end{matrix}
$$

#### Termination Condition
Don't stop when we add the goal to the fringe, only stop when we take out a node labeled with a goal from the fringe.
- The fringe is not FIFO - it is possible that the goal we added is not the one that wil come out first

**Properties:**
- **[[#**Optimal **|Optimal:]]** NO
	- [[#Heuristics|Heuristics]] might lead you on a non-optimal path or goal.
- **[[#**Spatial/Space Complexity**|Space]] & Time Complexity:** Range Between ($BFS\Longleftrightarrow DFS$)
	- If the [[#Heuristics|heuristic]] is good, it can be any
	- If the [[#Heuristics|heuristic]] is bad, closer to DFS or worse
		- *Insight*: DFS and BFS are [[#Heuristics|heuristic]] search with particular [[#Heuristics|heuristic's]]
- **[[#**Complete **|Complete:]]** NO
	- If you are following the standard tree search algorithm, you will not get stuck, however; you can end up endlessly deep like in a DFS.





---
### Admissible heuristics







---
### ### **Definitions**

 ###### **Rational Agent:** 
 - A rational agent is an entity (especially in artificial intelligence or economics) that selects actions to maximize its expected utility or achieve its goals, based on its current information and preferences.

###### **Complete:** 
- A search algorithm is **complete** if it is guaranteed to find a solution in a finite amount of time, provided that a solution exists.

###### **Optimal:** 
- The tree is structured to provide the minimum possible expected search time.

###### **Spatial/Space Complexity**:
- Measures the memory an algorithm needs relative to its input size to complete.

****