#### What is a search problem?
A search problem consists of three aspects
1) A State space
		State space defines the space (3d, 2d, node, etc...) that the agent is currently in. This is how we can define the parameters for our search problem to function.
2) A successor function
		A successor function allows us to create/define connections between state spaces.
3) A start state and a goal test
		The goal test is how we will 'test' the current state to see if it is the goal state we want our agent to end up at. 

The solution is a sequence of actions which transforms the start state to a goal state.

#### What's in a State Space?
There are two states to be aware of:
1) World State:
	This includes every last detail of the environment.
2) Search State:
	This keeps only the details needed for planning by abstracting the data to keep only the pertinent information.


#### What is a State Space Graph?
A state Space Graph is a mathematical representation of a search problem.
	Nodes are abstracted world configurations.
	Edges represent successor functions

A search tree defines the start node and branches to all possible futures.
- Important to note **we can never build the whole tree.**

###### Depth First Search
Graph traversal algorithm that explores as far as possible along each branch before backtracking. $O(b^m)$ where m is the number of nodes on layer b we are allowing the tree to grow too. ~7 is the cut off.
1) Visits the current node
2) Marks as visited
3) Recursively explore each unvisited node
4) Backtrack when it hits a dead end.

###### Breadth-First Search
Graph traversal algorithm that explores **all the neighbors** at the present depth level before moving on to nodes at the next level..  $O(b^s)$ where s is the number of neighbors on layer b.
1) Visits the current node
2) Marks as visited
3) While the queue is not empty
	1) Remove the first node from the queue
	2) Visit all of its unvisited neighbors
	3) Add those neighbors to the back of the queue

###### Uniform Cost Search
Graph traversal algorithm used to find the least-cost path from a start node to a goal node. $O(b^{C^*/\epsilon})$ where $C^{*}/\epsilon$ is the "effective depth" and b is the number of nodes on that depth.
1) Start at the initial node and put it in a **priority queue**, with its cost = 0.
2) Repeat until the queue is empty:
	1) Remove the node with the **lowest cost**.
	2) If it's the **goal node**, return the path.
	3) Otherwise, expand it:
		1) For each neighbor, compute the total cost so far.
	    2) Add the neighbor to the priority queue **if** it hasn’t been visited **or** if this path is cheaper than any previously recorded path to it.

## Informed Search

###### Heuristic Search function:
A function that estimates how close a state is to a goal.
- Manhattan Distance
- Euclidean Distance

###### Greedy Search Function:
While creating a state space graph, this will only expand the node that 'seems' to be the closest.
1) Expand the node you think is the closes to a goal
2) Use Heuristics to estimate the distance to goal for each state

###### A* Search:
This search function is a combination of the Uniform Cost function $g(n)$ and the Greedy Search function $h(n)$ meaning its run time is then $f(n) = g(n)+h(n)$. We only stop when we dequeue a goal from our queue.

![[Pasted image 20250423220337.png]]

