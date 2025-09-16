## 1) Uniform Cost Graph Search:
Consider the map below. Let us assume that you want to go from **Miami** $\to$ **Orlando**. Trace the path planning process using **uniform cost graph search**. At **each step**, show the currently **expanded node, the fringe and the closed set**. The format should be: **Step 79: Expanded: Dagobah:10, Fringe={Coruscant:34, Hoth:45}, Closed={Miami:0, …}** Where in the Planet: value, the value shows the current cost.
![[Pasted image 20250915164016.png]]

---
##### Criterion for Adding or Updating the Fringe for a UCGS
1) If a node is **not yet in the fringe** or a closed set $\Rightarrow$ **Add** to fringe
2) If a node is **already in the fringe** but you discover a path with a *lower* total cost $\Rightarrow$ **Update** fringe
3) If a node is **already in closed set** $\Rightarrow$ Do **NOT** add to fringe
---
## Attempt 1:
1. ✔️Fringe = {Miami:0}, Closed = {}

2. ✔️Expanded = Miami:0
	- Fringe = {Rivendell:1, Tatooine:5}
	- Closed = {}

3. Expanded = Rivendell:1
> [!Even though we have not expanded the Tatooine node yet, since the Tatooine node is within the Fringe we do not re add it to the Fringe.]
> - Fringe = {Tatooine:5, Tatooine: 6, Hogwarts: 8, Orlando: 11}
- Closed = {Miami:0}

---
## ✔️Attempt 2:
1. ✔️Fringe = {Miami:0}, Closed = {}

2. ✔️Expanded = Miami:0
	- Fringe = {Rivendell:1, Tatooine:5}
	- Closed = {}

3. ✔️Expanded = Rivendell:1
	- Fringe = {Tatooine:5, Hogwarts: 8, Orlando: 11}
	- Closed = {Miami:0}

4. ✔️Expanded = Tatooine:5
	- Fringe = {Hogwarts: 8, Orlando: 11}
	- Closed = {Miami:0, Rivendell:1}

5. ✔️Expanded = Hogwarts: 8
	- Fringe = {Orlando: 11}
	- Closed = {Miami:0, Rivendell:1,  Tatooine:5}

6. ✔️Expanded = Orlando: 11
	- Fringe = {}
	- Closed = {Miami:0, Rivendell:1,  Tatooine:5, Hogwarts: 8}

---
## 2) Heuristics
You are starting a new company where you plan to deliver packages door to door using your 1988 Honda Civic. You plan to use A* search to find the path that takes you to your destination in the shortest amount of time. **Discuss the following proposed heuristics**. Which are appropriate and which one is the best one?

- **(a)** $\mathbf{H_1}$**:**$\mathbf{h(x)=-1}$
	- Negative heuristics means you will go in circles
- **(b)** $\mathbf{H_2}$**:**$\mathbf{h(x)=0}$
	- An $h(x)=0$ reverts your $A^*$ back into $UCS$ 
- **(c)** $\mathbf{H_3}$**:**$\mathbf{h(x)=}$ Whatever time-by-car Google Maps gives you from the current location to the destination.
	- This is most likely the $h^*(n)$ value to use within your $hashmap\therefore$ this is the best one.
- **(d)** $\mathbf{H_4}$**:**$\mathbf{h(x)=H_3*2}$
	- This is a Pessimistic heuristic, meaning it will trap good paths too far down on the fringe.

---

