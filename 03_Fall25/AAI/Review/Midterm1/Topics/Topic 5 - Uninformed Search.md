Uninformed Search consists of creating a model of the agent and the world with which the agent persists in and searching for a plan on actions for the agent to take in order to reach a goal. The goal we are trying to reach has not been given to us and we must determine it based on the approach provided.

### Agents:
**Reflex**:
A reflex agent chooses an action based on its current observation (and maybe memory). After each action and observation the agents memory and is updated and the next action is decided once again. This does **not** consider the future consequences of actions.

- Are reflex agents **[[#Rational Agent A rational agent is an entity (especially in artificial intelligence or economics) that selects actions to maximize its expected utility or achieve its goals, based on its current information and preferences.|rational]]**?
	- Well chosen reflex agents go very far and many animals might be reflex agents, humans have many reflexive behaviors.

**Planning**:
A planning agent creates its set of actions based on the current observations at the time; this set of actions is known as the agents $plan$ which the agent executes during execution time.

- Using a world model $\mathbf{T(s,a)}\to s^\prime$, which tells us how the world evolves in response to actions, make decisions based on the hypothesized consequences.

---
### Plans:
Agents are able to create 1 of 3 **plan**:
1) **Partial plan:** does not reach the goal.
2) **[[#**Complete **|Complete]] plan:** reaches the goal at the end.
3) **[[#**Optimal **|Optimal]] plan:** Additional optimization criteria to guide the agent along.
	- Lowest cost
	- Lowest number of actions
	- Preferred states 
	- etc...

##### Re-planning:
This is a concept that involves redoing the planning whenever situations diverge from what was expected.
You can create **Contingency Plans**, which are plans created ahead of time that account for possible negative events, which help account for unexpected events. Furthermore, you can also use **Model predictive control** which involves creating a plan using a planning agent and adapting that plan every action taken.

---
###  Model vs World state:
A **problem of searching** for a plan consists of:
- State space: $S=\{s_1,s_2,...\}$
- Successor function: $T(s,a)\to s^\prime$
- Start state: $s_0$
- Goal test: $G(s)\to\{true,false\}$
The **Solution** is found when a plan transforms the start state to a goal state.

The search problem is a **model** that captures the aspects of the world useful for the solution and ignoring the rest, there are two states that we must track through models within our problem:
1) **World State -** Always a very large and complex model of the world
2) **Model State -** A more refined and tailored model to the problem statement.

##### Considerations:
**Exponential explosion**
1) Every time a **feature** might or might not be present, it doubles the state space creating the worry for exponential explosion of states. Furthermore, building the entire state space graph explicitly is often impossible
2) Many cases, states, and transitions are only revealed during the search
---
### General Search Tree:
**Strategy:**
- How to pick the next node from the fringe
- The fringe, as a data structure, should support the strategy taken
**Determines:**
- Solution found?
- Optimal?
- Max Iterations?

**Strategy:**
- [[#**Complete **|Completeness]]: guaranteed to find a solution if one exists?
- [[#**Optimal **|Optimal]]: least cost plan?
- Time Complexity?
- Space Complexity?
- $b\to$ Branching Factor
- $m\to$ Max Depth
- Total Nodes $\to O(b^m)$?

**Algorithm:**
1) Consider nodes as partial plans, starting from root.
2) Moving from a node to its children is called **expanding** a node.
3) Maintain a collection data structure called the **fringe** which are the nodes we need to expand.
4) Finally, stop when we found **a complete plan.**

##### Considerations:
It can get infinitely large if there is a loop within the state graph and it is unlikely that we will build it completely.

```
function TREE_SEARCH({S, T, s_0, G}, strategy):
	fring = {s_0}
	loop:
		if fring == {} return failure
		choose node n from fringe according to strategy
		if G(n) return solution
		remove n from fringe
		create successor nodesof n based on T(n) and add them to fringe
```

---
### Depth first tree search:
**Strategy:** expand a **deepest** node first on the left most side of the tree
- **LIFO**
**Fringe:** Space Complexity $\mathbf{=\mathcal{O}(bm)}$ it contains **siblings of the current path**
- Stack

**Properties**
- **[[#**Complete **|Complete]]:** NO
	- $m$ can be $\infty$
- **[[#**Optimal **|Optimal]]:** NO
	- **Left Most Solution**
- **DFS?**
	- Some **left prefix** of the tree
	- Could process $\mathcal{O}(b_m)$
- **[[#**Spatial/Space Complexity**|Space Complexity:]]**
	- **Fringe ONLY**
	- Has the **siblings of the current path** to root $\mathbf{\mathcal{O}(bm)}$
![[Depth-First-Tree-Traversal.gif]]
---
### Breadth first tree search:
**Strategy:** expands all nodes **above the shallowest solution**, which is at **depth** $\mathbf{s}$
- **FIFO**
**Fringe:** Space Complexity $\mathbf{=\mathcal{O}(b^s)}$ it contains all nodes above the **shallowest** **solution** at **depth** $\mathcal{s}$
- Queue

**Properties:**
- **[[#**Complete **|Complete]]:** YES
	- When it reaches $\mathcal{s}$ it will find the **optimal** solution
- **[[#**Optimal **|Optimal]]**: YES
	- It will wind the shallowest solution
- **[[#**Spatial/Space Complexity**|Search & Space Complexity]]:****
	- Both **Search Time** and **Space Complexity** are $\mathcal{O}(b^s)$
![[Breadth-First-Tree-Traversal.gif]]
---
### [[#Depth first tree search|Depth first]] vs. [[#Breadth first tree search|Breadth first]] search:
$$
\begin{matrix}
\begin{matrix}
\mathbf{\text{When will BFS outperform DFS?}}\\
\cdot\text{ Few solutions are few but near.}\\
\cdot\text{ DFS gets lost and stuck in loops.}
\end{matrix}
&&
\begin{matrix}
\mathbf{\text{When will DFS outperform BFS?}}\\
\cdot \text{ Many Solutions but far between.}\\
\cdot \text{ Keep Going in any direction.}
\end{matrix}
\end{matrix}
$$

### Iterative deepening:
DFS has the advantage of a low spatial complexity however is it possible to get this advantage within BFS's shallow-solution advantages?

**Iterative Deepening:**
1) `Run a DFS with a d=1` $\therefore \mathcal{O}(b)$, if no solution:
2) `Run a DFS with a d=2` $\therefore \mathcal{O}(b+1)$, if no solution:
3) ...

**Gain** low space complexity of DFS however we loose the represented traversal of the upper parts of the tree every iteration of the loop.

---


### Uniform cost search (UCS):
**Cost - based search:**
While [[#Breadth first tree search|bread first search]] finds the **shortest plan** in terms of number of actions many times we want to choose an action based upon the cost of the action. Often times we are searching for a plan with the lowest cost where the costs are adding **(Dijkstra's)**.

A variant of general tree search that assumes **actions have cost $\mathbf{c(a)}$**. For each node $n$, keep the cumulative cost of actions from the root $g(n)$. Implementing the **fringe as a priority queue**, investigate partial plans in **order of their costs**.


**Effective Depth:**
Assuming your cheapest solution has a cost of $C^*$ and each action has a cost of at least $\mathcal{E}$, the the deepest your search can be is $D_{eff}=\frac{C^*}{\mathcal{E}}$. If a node has been **expanded** and later on another node connects to that **previously expanded node** that node is **NOT** re added to the fringe.

**Properties:**
- **[[#**Complete **|Complete]]:** YES
	- Assumptions: $\mathcal{E}>0 \text{ and } C*$ is finite
- **[[#**Optimal **|Optimal]]**: YES
	- It will find the shallowest solution
- **[[#**Spatial/Space Complexity**|Search & Space Complexity]]:****
	- Both **Search Time** and **Space Complexity** are $\mathcal{O}(b^\frac{C^*}{\mathcal{E}})$

---
### **Definitions**

 ###### **Rational Agent:** 
 - A rational agent is an entity (especially in artificial intelligence or economics) that selects actions to maximize its expected utility or achieve its goals, based on its current information and preferences.

###### **Complete:** 
- A search algorithm is **complete** if it is guaranteed to find a solution in a finite amount of time, provided that a solution exists.

###### **Optimal:** 
- The tree is structured to provide the minimum possible expected search time.

###### **Spatial/Space Complexity**:
- Measures the memory an algorithm needs relative to its input size to complete.