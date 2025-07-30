# Vocab

**What is an OS?**
- An interrupt drive program
**What is a VM?**
- A software implementation of a hardware ISA
**Assembler**
- A program that translates assembly language into object code.

**Linker**
Linkers are programs which can take two or more object code files to create a single executable file.
- Dynamic Linker:
	-  
- Static Linker:
	- The process of combining two or more object codes into a single executable file is called static linking


**Loaders:**
Loaders are programs whose main task is to store an executable file in the computer memory for execution.
- **Absolute Loader:**
	- Load a program into a specific memory location chosen by the programmer.
- **Bootstrap Loaders:**
	- Stand-alone programs not residing in memory which are used to boot the computer system and load the OS.
- **Relocating Loaders:**
	- A dynamic loader that loads a program in any memory location where there is room available.

**Concurrency:**
- **Apparent concurrency:**
	- Two or more programs residing in memory at the same time share the CPU by interleaving instructions.
- **True Concurrency:**
	- Two or more processes carry out different activities on different devices at the same time.



---

# Practice Test

1) When generating code for instruction $LOD$ and $STO$ (in your compiler) a lexicographical level must be generated to indicate whether the top of the stack value is loaded or stored locally (current activation record) or it has to be stored to or loaded from another activation record.
	 1) How is the lexicographical level calculated in instructions $LOD$, $STO$, and $INC$?
		 - 
	 2) How does your compiler keep track of the current lexicographical level?
		 - 

2) On operating Systems:
	1) What is an Operating System?
		- An event driven program
	2) What are the three main characteristics of an Operating System?
		- Create a friendly interface between user and computer system.
		- Manage system resources efficiently.
		- Create an environment for other programs to run.

3) On Interrupts:
	1) When a running process initiates an I/O operation an interrupt occurs. What is the name of the interrupts?
		- 
	2) Assume that process P1 is in the waiting for I/O state, P3 is in the ready state, and process P2 is running. In this scenario, an I/O interrupt, a timer interrupt, and a system call (SIO) occur simultaneously. The OS must handle all interrupts. Describe in one short sentence each step carried out by the OS.
		- 

4) Process Synchronization
	1) A running process executes a $P(S)$ operation. Does it block?
		- 

5) The run time environment is composed of five segments:
	- `CODE(TEXT)`:
		- The machine instructions of your program.
	- `DATA`:
		- Global and static variables that are explicitly initialized in your source.
	- `BSS`
		- Global and Static variables that are uninitialized or initialized to 0.
	- `HEAP`:
		- Dynamically allocated memory at runtime.
	- `STACK`:
		- Activation Records, Local Variables, Return and Saved addresses.

	You have to tell in what segment you will place each one of the following examples:
	- `int seven = 7;` $\to$ `DATA`
	- `seven = seven+7;` $\to$ `CODE`
	- `seven=7;` $\to$  `CODE`
	- `int seven;` $\to$ `BSS`
	- `malloc(seven);` $\to$ `HEAP`


6) Draw a diagram showing the `ELF (object code)`, Process Control Block, Thread Control Blocks, and the run time environment for a program with two threads, Indicating: how these data structures are related. Use arrows to show all relationships. Name all fields of the TCB and at least 2 of the PCB.


7) Draw a diagram showing the states a process can be in and indicate what is the event (interrupt) that moves the process from one state to another. Use the states explained in class. If you use a new state, which was not explained in class, you must explain how the new interrupts work.


8) Assemblers and code generation
	- Assume you are given the following program in PL/0 to be compile in your HW3:
```
var else, x, call;
x := call+5 * else.
```
- Translate it into assembly language. Use the ISA of your virtual machine.

	- The ISA for Virtual Machine is defined as follows:
		- OP $\to$ The Opcode that will be executed
		- L $\to$ Lexicographical level
		- $M$ $\to$ Sub operation that depends on Opcode

	- Furthermore, there are three items we must account for within the stack:
		- $SL\to$ Static Link, Callers Base pointer of the lexical parent
		- $DL\to$ Dynamic Link, Callers old Base Pointer $(BP)$
		- $RA \to$ Return Address, Callers old Program Counter $(PC)$

- With this being said we can now construct our Assembly Language based on the provided PL/0 code:
```
INC 0 6
LOD 0 3
LIT 0 5
ADD 0 1
LOD 0 3
MUL 0 2
STO 0 4
```

9) What is an EOC interrupt?