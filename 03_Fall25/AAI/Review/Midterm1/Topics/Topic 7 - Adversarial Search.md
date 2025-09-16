In our prior searches we were planning all actions ahead of time however this will not work because **there are other agents who take actions in opposition to our goals**. We need to react to the actions of the other agents, paradoxically: a [[Topic 5 - Uninformed Search#Agents|reflex agent]], with a lookup table for every state might work (but would be very inefficient)

### Game playing in AI
The AI agent is one of the players, assuming we have two players $\{A,B\}$, who take actions successively:
$$\tag{Actions}
s_0\to a_{A1}\to s_1 \to a_{B1}\to s_2 \to a_{A2}\to etc...$$
Usually, we cannot search for a **plan** due to the fact that the **agent's** actions are interleaved within the opponent's actions $\therefore$ we must search for a **[[#**Policy **|policy]]** $(\pi(s)\to a)$ instead. Take actions to maximize the utility of the terminal state you reach, a perfect player at any choice chooses the one with `max(value)`.


### Types of Games:
- Is you game **Deterministic** or **Stochastic**?
	- **Deterministic:** An algorithm consistently produces the exact same output for a given input, with no randomness or variation
	- **Stochastic:** A system or process that involves randomness, unpredictability, or probability.
- How much **information is provided**?
- Amount of players
- etc...

---
### Deterministic games:
A deterministic game is a game that an algorithm can consistently produce the exact same output for a given input, with no randomness or variation. With that being said, we can say that the only input needed for a deterministic game is:
- State's $\Longrightarrow S=\{s_0,...,s_n\}$
- Player's $\Longrightarrow P=\{1,...,N\}$, take turns
- Action's $\Longrightarrow A=\{A_1,...,A_N\}$
	- What actions are available for what player at what state.
- Transition Function $\Longrightarrow T(s,a)\to s^\prime$
- Terminal test: $completed(s)\to\{true,false\}$
- (Terminal) **utilities:** $U(s,p)\in\mathbb{R}$

#### Single Player Deterministic game:
**[[#Policy |Policy]]** should be
- Take the action for which the successor has the largest value:
$$
\tag{Policy}
\pi(s)=argmaxV(T(s,a))
$$
This is **BOTH** gameplay and planning as you can now create a list of actions to the end of the game.

#### Two player Deterministic, [[#**Zero Sum **|zero-sum]] game:
Agents have opposite utilities $\therefore$ for each terminal state they add up to zero:
$$U(s,p_1)=-U(s,p_2)$$
One player is **minimizing** the agents utility while the other player is trying to **maximize** the agents utility.
![[Pasted image 20250915193944.png]]

---
### Adversarial Search (a.k.a Minimax):
This search is used for deterministic, zero sum games; we have *Player 1* who is the **maximizing player** $(\Delta)$ and the **minimizing player** $(\bigtriangledown)$. To conduct this search you create a **Minimax search tree** which is a **state-space search tree** with a **V value**. In this search tree players alternate turns operating a value $V$. This style of search works perfectly for an opponent that plays perfectly.

**Properties:**
- **[[#**Spatial/Space Complexity**|Space]] Complexity**: $\mathcal{O}(b^m)$
- **Time Complexity:** $\mathcal{O}(bm)$
	- Where:
		- $b\to$ Branching Factor
		- $m\to$ Max Depth

 **Algorithm:**
```
def maxvalue(s)
	if s terminal return val(s)
	v=-infty
	for s' in succ(s)
		v = max(v,minvalue(s'))
	return(v)
	
def minvalue(s)
	if s terminal return val(s)
	v = infty
	for s' in succ(s)
		v = min(v,maxvalue(s'))
	return(v)
```

---
### Alpha-beta pruning implementation


 **Algorithm:**
 ```
 def maxvalue(s, alpha, beta):
	 if s terminal return val(s)
	 v = -infty
	 for s' in succ(s)
		 v = max(v, minvalue(s', alpha, beta))
		 if v >= beta return v
		 alpha = max(alpha, v)
	return v
	
def minvalue(s)
	if s terminal return val(s)
	v = infty
	for s' in succ(s)
		v=min(v, maxvalue(s',alpha,beta))
		if v <= alpha return v
		beta = min(beta, v)
	return v
 ```



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

###### **Heuristics:**
- Formally defined as a **strategy or guideline** that helps you make progress toward a solution quickly, even if it doesn’t guarantee the _best_ or _perfect_ answer.

###### **Policy:**
- A function that tells the AI what action to take for any possible game state. It allows adaptive decision-making in uncertain, adversarial environments.

###### **Zero Sum:**
- Situation in which one person's gain is precisely equal to another person's loss
