# Virtual Machines as Software Interpreters
The Psuedo-code (P-code) is a virtual machines which is a software implementation of an instruction set architecture. P-code was implemented in the 70s to getnerate intermediate code for Pascal compilers. An example of a P-code virtual machine is the Java Virtual Machine (JVM), whose language is commonly referred to as Java Bytecode.

The ISA of the PM/0 has **24 instructions** and the instruction format has **3 components**:
- **OP** $\rightarrow$ operation code
- **L** $\rightarrow$ lexicographical level
- **M** $\rightarrow$ multiple meanings depending of the opcode:
	- A **number** If opcode is:
		- LIT, INC
	- A **program address** if opcode is:
		- JMP, JPC, CAL
	- A **data address** if opcode is:
		- LOD, STO
	- The identity of the operator 
---
# P-code: Instruction Set Architecture
The interpreter of the P-machine(PM/0) consists of a **process address space (PAS)**. The PAS is a memory area which consists of two segments:
1) **Text Segment** - Contains the instructions.
2) **Stack Segment** - Contains the action records.

The **CPU** has **four registers:**
1) **Base Pointer (BP) -** Which points to the base of the current Activation Record (AR) within the stack segment.
2) **Stack Pointer (SP) -** Which points to the top of the stack segment. 
3) **Instruction Pointer A.K.A Program Counter (PC) -** Which points to the next instruction to be executed.
4) **Instruction Register (IR) -** Where instruction fetched from memory are placed into.

## Activation Records
Activation Record is the name given to a data structure which is inserted in the stack each time a procedure or function is called. The AR contains information to control sub routine linkage as well as reserves space for local variables and parameters such as:
- **Parameter**
	- Space reserved to store the actual parameters of a function.
- **Locals**
	- Space reserved to store the local variables within the function/procedure.
- **Return Address**
	- An **RA** points to the next instruction to be executed in the calling function after termination of the current function/procedure.
- **Dynamic Link**
	- Points to the base of the previous stack frame.
- **Static Link**
	- Points to the stack frame of the procedure that statically encloses the current function.
- **Functional value**
	- Location to store the function returned value.
---
# The Instruction Format
The P-machine instruction cycle has two steps known as:
### Fetch
- In this step, an instruction from the text segment is 'fetched' and the program counter is incremented.
### Execute
- In this step `ir.op` indicates the operation to be executed.

| Index: | Example: | Explanation:                                                         |
| ------ | -------- | -------------------------------------------------------------------- |
| 01     | INC 0,M  | Increment sp by M                                                    |
| 02     | OPR 0,M  | [[03_Virtual Machines#02-OPR]]                                       |
| 03     | LOD L,M  | Push from location at offset M in stack frame L levels down          |
| 04     | STO L,M  | Store value on top of stack at offset M in stack frame L levles down |
| 05     | CAL L,M  | Call procedure at M (generates new AR and pc = M)                    |
| 06     | LIT 0,M  | Push constant value M onto stack                                     |
| 07     | JMP 0,M  | pc = M                                                               |
| 08     | JPC 0,M  | Jump to M if top of stack element is 0                               |
| 09 - 1 | SYS 0,1  | Write the top stack element to the screen                            |
| 09 - 2 | SYS 0,2  | Read in input from the user and store it on top of the stack         |
| 09 - 3 | SYS 0,3  | End of Program (Set Halt flag to zero)                               |

## Example:
$$
\begin{equation}\tag{Ex.1}
01-\text{LIT}\;\;0\text{, M}
\end{equation}
$$
$$
\begin{equation}
01-\text{LIT}\;\;0\text{, 23}
\end{equation}
$$
When you receive LIT Op code, this stands for:
- **Push constant value M onto stack**
Therefore to do this you would do the following:
$$
\begin{equation}\tag{A.1}
\text{LIT}\;\;0\text{, M} \Rightarrow
sp\leftarrow sp+1 \;;\;
\text{stack[sp]}\leftarrow \text{M}
\end{equation}
$$
1) Increment Stack pointer (sp) by 1 to place the literal on top.
2) Place literal on top of the stack.

### 02-OPR
If you receive an OPR that is $\mathbf{02}$ then you will do an operation using the stack:




# Assembly Language