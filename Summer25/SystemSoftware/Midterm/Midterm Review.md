# 1) Virtual Machines:

1) **What is a Virtual machine? (Choose all that are correct)**
	- A software implementation of a compiler.
		- 
	- A simulator of a hardware.
		- 
	- An software implementation of a CPU, hard drives, and I/O devices.
		- 
	- As emulator of an ISA.
		- 
	- A software Implementation of an ISA
		- 

2) **Why is it an error to implement instruction in a virtual machine (HW1) using functions?**
	- Within a virtual machine you have to implement a **fetch-execute cycle** on the simulated stack and registers. If you are to implement separate functions for the instructions you then hand control to the host machine. Once this happens you no longer control when or how the host compiler adjusts its own stack pointer, therefore the BP, SP, and stack contents after each step would be wrong.
---
# 2) Transition Diagrams:

1) Give a **Transition Diagram** for comments in langauge M. We are interested in comments of the type: `*$ comments... $*`.
![[Pasted image 20250617001449.png]]

2) Give a **Transition Diagram** to recognize that the number of 1's in a sequence is a multiple of four. $\Sigma = \{0,1\}$.
![[Pasted image 20250617001947.png]]

---
# 3) Grammar

##### What is left recursion?
- Left recursion occurs when a **non-terminal** symbol can eventually call itself on the left side of a production, causing infinite recursion in **top-down parsers.**
- This is an issue because it will lead to infinite recursion within the parser due to it calling the same rule without consuming any input.
	- Example:
		- $A\rightarrow A\alpha | \beta ==\Rightarrow Expr → Expr + Term | Term$ 
		- Where A is your non-terminal, it will repeatedly call the expression as it is the first thing within the grammar resulting in:
			- $Expr → Expr + Term$
				    $→ Expr + Term + Term$
				    $→ ...$
		- In order to transform this and end the left recursion we introduce a NEW non-terminal:
		- $A  → β A'$
		 $A' → α A' | ε$
			- The new non-terminal $(A^\prime)$ prevents left recursion by introducing $\epsilon$ $(\text{null string})$ it is a cancellation of the sequence and ends the recursive calls.


1) Given the following grammar, rewrite the grammar to avoid left recursion:
	- $A\rightarrow A;B|B$
	- $B\rightarrow B,A^\prime | A^\prime$
	- $A^\prime \rightarrow (A)|a$

2) Given the following grammar, rewrite the grammar to avoid left recursion:
	- $A\rightarrow A\#B|B$
	- $B\rightarrow B\&A^\prime | A^\prime$
	- $A^\prime \rightarrow (A)|a$

---
# 4) Stack Mechanism

1) Where do we get the information stored in the return address and dynamic link when a function is called? Why do we need to save it in the activation record?
	- I am not asking where RA and DL are pointing to. If you answer telling where they are pointing to, your grade for this question is zero.


