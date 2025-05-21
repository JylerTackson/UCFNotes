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
# P-code: Instruction Set Architecture
The interpreter of the P-machine(PM/0) consists of a **process address space (PAS)**. The PAS is a memory area which consists of two segments:
1) **Text Segment** - Contains the instructions.
2) **Stack Segment** - Contains the action records.

The **CPU** has **four registers:**
1) **Base Pointer (BP) -** Which points to the base of the current Activation Record (AR) within the stack segment.
2) **Stack Pointer (SP) -** Which points to the top of the stack segment. 
3) **Instruction Pointer A.K.A Program Counter (PC) -** Which points to the next instruction to be executed.
4) **Instruction Register (IR) -** Where instruction fetched from memory are placed into.
# The Instruction Format

# Assembly Language