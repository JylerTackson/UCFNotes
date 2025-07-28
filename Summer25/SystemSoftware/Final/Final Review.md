1) When generating code for instruction $LOD$ and $STO$ (in your compiler) a lexicographical level must be generated to indicate whether the top of the stack value is loaded or stored locally (current activation record) or it has to be stored to or loaded from another activation record.
	 1) How is the lexicographical level calculated in instructions $LOD$, $STO$, and $INC$?
	 2) How does your compiler keep track of the current lexicographical level?

2) On operating Systems:
	1) What is an Operating System?
	2) What are the three main characteristics of an Operating System?

3) On Interrupts:
	1) When a running process initiates an I/O operation an interrupt occurs. What is the name of the interrupts?
	2) Assume that process P1 is in the waiting for I/O state, P3 is in the ready state, and process P2 is running. In this scenario, an I/O interrupt, a timer interrupt, and a system call (SIO) occur simultaneously. The OS must handle all interrupts. Describe in one short sentence each step carried out by the OS.

4) Process Synchronization
	1) A running process executes a $P(S)$ operation. Does it block?

5) The run time enlivenment is composed of five segments