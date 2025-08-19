# 1) Virtual Machines:

1) **What is a Virtual machine? (Choose all that are correct)**
	- A software implementation of a compiler.
		- **FALSE**
			- A compiler translates the high-level code (C, C++, Java) into low level machine code; where as the VM executes the machine code. Furthermore a compiler is already implemented as software.
	- A simulator of a hardware.
		- **TRUE**
			- A VM can be thought of as an entire computer that is simulated within the environment that is running the VM program.
	- An software implementation of a CPU, hard drives, and I/O devices.
		- **TRUE**
			- Since the above statement is true this one must be true. A VM needs hard drives to store date, I/O devices to be interacted with, and finally a CPU to execute any given orders.
	- As emulator of an ISA.
		- **TRUE**
			- An ISA stands for Instruction Set Architecture - this refers to the Instruction set corresponding to the VM that is being emulated. In assignment 1, we were given a specific ISA and we executed it using a switch statement through the Fetch-Execute cycle.
	- A software Implementation of an ISA
		- **TRUE**
			- As pointed out previously, the VM is emulating a CPU within an actual computer therefore it is entirely running through software implementation. This means that the ISA being emulated through the VM must also be implemented through software.

2) **Why is it an error to implement instruction in a virtual machine (HW1) using functions?**
	- Within a virtual machine you have to implement a **fetch-execute cycle** on the simulated stack and registers. If you are to implement separate functions for the instructions you then hand control to the host machine. Once this happens you no longer control when or how the host compiler adjusts its own stack pointer, therefore the BP, SP, and stack contents after each step would be wrong.
---
# 2) Transition Diagrams:

1) Give a **Transition Diagram** for comments in language M. We are interested in comments of the type: `*$ comments... $*`.
![[Pasted image 20250617001449.png]]

2) Give a **Transition Diagram** to recognize that the number of 1's in a sequence is a multiple of four. $\Sigma = \{0,1\}$.


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
	- $A\rightarrow \text{A ;B|B}$
	- $B\rightarrow B , A^\prime | A^\prime$
	- $A^\prime \rightarrow\text{ (A)|a}$
	
	- Answer:
		- $A\rightarrow BC$
		- $C\rightarrow ;BC|\epsilon$
		- $B\rightarrow B^\prime A^\prime$
		- $B^\prime \rightarrow ,A^\prime A^\prime | \epsilon$
		- $A^\prime \rightarrow (A)| a$

2) Given the following grammar, rewrite the grammar to avoid left recursion:
	- $A\rightarrow A\#B|B$
	- $B\rightarrow B\&A^\prime | A^\prime$
	- $A^\prime \rightarrow (A)|a$
	
	- Answer:
		- $A\rightarrow BC$
		- $C\rightarrow \#BC|\epsilon$
		- $B \rightarrow A^\prime B^\prime$
		- $B^\prime \rightarrow \&A^\prime B^\prime | \epsilon$
		- $A^\prime \rightarrow (A)|a$
---
# 4) Stack Mechanism

### P-Machine Architecture:
- Base Pointer **(BP):** Points to the base of the current Activation Record.
- Stack Pointer **(SP):** Points to the current top of the stack.
- Program Counter **(PC):** Points to the next instruction to be executed.
- Instruction Register **(IR):** Stores the instruction to be executed.
~~-----------------------~~
### What is an Instruction Register?
- An instruction Register contains the components for the ISA of the emulated VM. For the P-Machine, the IR contained the following components:
	- Operation Code **(OP):** Indicated the operation to be executed
	- Lexicographical Level **(L):** Scope level (stack frame level).
	- Operator Dependent Instruction **(M):** This value was dynamic dependent on the OP value, it could contain any of the following:
		- A number (when OP is LIT or INC)
		- A program address (when OP is JMP, JPC, or CAL)
		- A data address (when OP is LOD or STO)
		- The identity of the arithmetic/relational operation associated to the OP
			- (OPR 0 2 (ADD) or OPR 0 4 (MUL))
~~-----------------------~~
### What is an Activation Record:
An **activation record** (also known as a **stack frame**) is a data structure used at runtime to store information about an active function or procedure call. It contains everything needed to execute the function correctly such as:
- Return Address **(RA):** The address in the program where execution resumes after the current function finishes.
- Dynamic Link **(DL):** A pointer to the activation record of the calling function.
- Static Link **(SL):** A pointer to the top of the stack.
- Parameters: The arguments passed to the function or procedure.
~~-----------------------~~

1) Where do we get the information stored in the return address and dynamic link when a function is called? Why do we need to save it in the activation record?
	- I am not asking where RA and DL are pointing to. If you answer telling where they are pointing to, your grade for this question is zero.
	
		- 

---
# 5) Regular Expression

1) Give a Regular Expression to recognize that the number of 2's in a sequence is a multiple of three.
   $\Sigma=\{0,1,2\}$
	$$
	\begin{equation}\tag{A.5}
	R_{5} = ((0|1)^*2(0|1)^*2(0|1)^*2)(0|1)^*
	\end{equation}
	$$
	- We are just looking for a sequence of 2's that is divisible by 3 this means that there can be symbols between the 2's however in the end there must be a sequence of 2's within the string that is divisible by three.

---
# 6) Scanner
Using the following table:
![[Pasted image 20250617214751.png]]
Translate the following two statements into tokens and indicate if any one of them generates an error message. If an error is found stop the translation
1) `if a > 4 then then a := a + 1`
	- "23 02 a 13 03 4 24 24 02 a 20 02 a ? 03 1"
		- Error: The symbol "+" is not in the symbol table.
2) `> if ; 1 * a then a ;  16 a`
	- "13 23 22 03 1 08 02 a 24 02 a 22 03 16 02 a"
		- No Errors.


Using the following table:
![[Pasted image 20250617215158.png]]
Translate the following two statements into tokens and indicate if any one of them generates an error message. If an error is found stop the translation
1) `if a > 4 then then a : = a * 1;`
	- "23 02 a 13 03 4 24 24 02 a 20 22 02 a 08 03 1 ?"
		- Error: The symbol ";" is not in the symbol table.
2) `> if 1 = a then a :=  16`
	- "13 23 02 1 22 02 a 24 02 a 20 22 03 16"
		- No Error

---
# 7) Symbol Table

How to build a Symbol Table:
1) Kind:
	- This refers to the "kind" of symbol, there are only three kind's.
		1) Const = 1
		2) Var = 2
		3) Proc = 3
2) Name:
	- This refers to the name of the variable or procedure that is being saved.
3) Value:
	- This is the value of the variable.
4) L:
	- This is the scope level of the current level or procedure.
5) Address:
	- This is the current index within the linear array.
6) Mark:
	- Always 0.

You will start with your table pointer at the top of the program and move it down line by line filling in the symbol table with each kind that needs to be filled in and its corresponding information.
Finally, since we are told that the activation record has DL and RA, we know that the very first index that will store a symbol is going to be 2 since 0 and 1 are taken.
When you go up a lexicographical level you are also going into a new activation record therefore you are going into a new linear array so the address's restart for the new level.

Given the following Program:
```
const k = 7;
var x, y;
Procedure sum;
   var y, x;
   begin
     **statements**
   end;
Procedure add;
   var w, y, x; <- 1 Populate symbol table up to this declaration.(including this variables)
   begin
     **statements**
   end;
begin  
  x:= 1;    
  call sum;
  call add;
end.
```
Using a linear array as Symbol Table(ST) and considering that each entry  in the ST has the following fields: kind, name, value, L, address, and mark; Show the state of the symbol table at point 1. Use  “?” for the procedure address.

Assume that the AR only has DL and RA.


| TP      | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| ------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Kind    | 1   | 2   | 2   | 3   | 2   | 2   | 3   | 2   | 2   | 2   |
| Name    | k   | x   | y   | sum | y   | x   | add | w   | y   | x   |
| Value   | 7   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
| L       | 0   | 0   | 0   | 0   | 1   | 1   | 0   | 1   | 1   | 1   |
| Address | 2   | 3   | 4   | ?   | 2   | 3   | ?   | 2   | 3   | 4   |
| Mark    | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |

---
# 8) Code Generation

![[Pasted image 20250617224108.png]]
![[Pasted image 20250617224145.png]]

Generate code for the following PL/0 program. Code must be generated for a VM with DL and RA only.
```
var x, y, w;
if x > w then begin
                        x:= 1+ 2;
                        y:= w + x
                     end.
```


**Main Activation Record:**

| Index: | Variable: |
| ------ | --------- |
| 4      | w         |
| 3      | y         |
| 2      | x         |
| 1      | DL        |
| 0      | RA        |
~~---------------------------------~~

| Op Code | L   | M   |
| ------- | --- | --- |
| INC     | 0   | 5   |
| LOD     | 0   | 2   |
| LOD     | 0   | 4   |
| GTR     | 0   | 9   |
| JPC     | 0   | 39  |
| LIT     | 0   | 1   |
| LIT     | 0   | 2   |
| STO     | 0   | 2   |
| LOD     | 0   | 4   |
| LOD     | 0   | 2   |
| ADD     | 0   | 2   |
| STO     | 0   | 3   |
| SYS     | 0   | 3   |

---
# 9) Stack Mechanism and Code Generation
Consider the program described below and give the generated code for the statements at 1, 2, and 3. Procedures are called as shown below.
```
            BIGSUB calls SUB2
            SUB2 calls SUB3
            SUB3 calls SUB1

(Assume the ARs have SL, DL, and RA. If errors occur, indicate where it is detected and what is the cause of the error.

procedure BIGSUB;
    var A, B, C : integer;
    procedure SUB1;
      var A, K : integer;
      begin { SUB1 }
      B := C + K;  <-----------------------1
      end;  { SUB1 }
    procedure SUB2(X : integer);
      var B, F, E : integer;
      procedure SUB3;
        var C, K, E : integer;
        begin { SUB3 }
        SUB1;
        K := E + B;   <--------------------2
        end; { SUB3 }
      begin { SUB2 }
      SUB3;
      A := E + K;  <-----------------------3
      end; { SUB2 }
    begin { BIGSUB }
    SUB2(9);
    end; { BIGSUB }
```

---
# 10) Stack Mechanism 
Show the stack contents (schematic) of the following program after four calls to the function factorial**. Then show the return sequence as well**. **Indicate where the SL, DL, and RA are pointing to (use arrows). Include FV and parameter as well in AR.**
```
Void main( ) {
    int value;
    int factorial (int n) { 
            If (n <= 1)
                return 1;
            else return (n * factorial(n – 1));
   } 
   value = factorial (4);
}
```

Important NOTES:
- The Static Link **(SL)** is always pointing to the caller function. In the case of recursion, the recursive function calls will always point to the main function that called the first recursive call. If we had a function call a function and then call another function, the static links would be pointing at the previous function that called it.
- The Dynamic link always points at the Bottom of the stack frame of the previous frame. In this case, the bottom is the function value which will hold the value of the returned recursive factorial value.

![[Pasted image 20250617231634.png]]

![[Pasted image 20250617231644.png]]
![[Pasted image 20250617231658.png]]
![[Pasted image 20250617231714.png]]
![[Pasted image 20250617231720.png]]


