# What is System Software?
A System Software consists of a set of programs that support the operation of a computer system.
- They help the programmer simplify the programming process.
- Create an environment to run application software efficiently.
	- **Program Development Environment:**
		- **Text Editor**
			- Software that permits the creation and editing of .txt files 
				- Application programs
		- **Compiler**
			- Translates programs written in high level to machine code a.k.a Assembly
		- **Assembler**
			- Translates programs written in assembly to object code (binary)
		- **Linker**
			- Combines and resolves references between object programs and creates executable code.
		- **Debugger**
			- Used to debug executable programs and their related object code and source program.
	- **Run-Time Environment:**
		- **Loader**
			- Loads an executable code and starts its execution.
		- **Libraries**
			- Pre-compiled programs that create a set of functions to be used by other programs.
		- **Dynamic Linker**
			- Loads and links shared libraries at **run-time**
		- **Operating System**
			- Event driven program that makes an abstraction of the computer systems. Handles all resources efficiently, creates an environment for application programs.


# The process of an interpreter:
## The structure of a tiny computer: 

**Von-Neumann Machine (VN)** created by **John Von Nuemann** is the theoretical computer scientists who created the idea of memory.
- **Program Counter (PC):** a register that holds address of the next instruction to be fetched and executed.
- **Memory Address Register (MAR):** a register used to select the address of a specific memory location in Main Storage (*RAM*) so that instructions or data can be written to or read.
- **Main Storage (MEM):** used to store programs and data; aka *RAM*
- **Arithmetic Logic Unit (ALU):** used to execute Arithmetic and logic instructions such as:
	- ADD or Subtract
	- $>$ or $<$
- **Instruction Register (IR):** A register stores the instruction to be executed by the process.
	- Two Fields, can be accessed using the selector operator ".":
		1) Operation (OP)
		2) ADDRESS
- **Decoder:** a circuit that decides which instruction the processor will execute. Takes instruction op-code from the **IR** as input and outputs a signal to the Control Unit to carry out the execution.
- **Accumulator (A):** the only register that can be used by user programs.
## A program of an isolated system:

**Fetch - Execute Cycle:** In the VN machine the instruction Cycle is defined by the following loop:
-  **Data Movement 1:** The transfer of the contents from **PC** into **MAR.**
	- $\mathbf{\text{MAR}} \leftarrow \mathbf{\text{PC}}$
- **Data Movement 2:** The transfer from a memory location **(MAR)** into the register **(MDR)**. The address of the memory location has been stored previously into the **MAR** register.
	- $\mathbf{\text{MDR}} \leftarrow \mathbf{\text{MEM[MAR]}}$
-  **Data Movement 2.1:** The transfer from a memory location **(MDR)** register to a memory location **(MAR)**. The address of the memory location has been previously stored into the **MAR** register.
	- $\mathbf{\text{MEM[MAR]}} \leftarrow \mathbf{\text{MDR}}$
- **Data Movement 3:** Transferring from **MDR** into **IR** is indicated as:
	- $\mathbf{\text{IR}} \leftarrow \mathbf{\text{MDR}}$
- **Data Movement 4:** The **operation field** of the **IR** register is sent out to the Control unit through a **DECODER**:
	- $\mathbf{\text{Control Unit}} \leftarrow \mathbf{\text{DECODER}} \leftarrow \mathbf{\text{IR.OP}}$
	- If the value of $\mathbf{\text{IR.OP}}==00$, the the decoder is set to execute fetch cycle again.
## The Instruction Format:
The Instruction Cycle is comprised of 2 primary components: the **Fetch** cycle which retrieves the instruction from memory, and the **Execution** cycle which carries out the execution of the instruction retrieved.

### **ISA - Instruction Descriptions:**

| opcode | mnemonic                       | meaning                                                                   |
| ------ | ------------------------------ | ------------------------------------------------------------------------- |
| 0001   | $\mathbf{\text{LOAD <x>}}$     | $\mathbf{\text{A}} \leftarrow \mathbf{\text{Mem[x]}}$                     |
| 0010   | $\mathbf{\text{ADD <x>}}$      | $\mathbf{\text{A}} \leftarrow \mathbf{\text{A}} + \mathbf{\text{Mem[x]}}$ |
| 0011   | $\mathbf{\text{STORE <x>}}$    | $\mathbf{\text{Mem[x]}} \leftarrow \mathbf{\text{A}}$                     |
| 0100   | $\mathbf{\text{SUB <x>}}$      | $\mathbf{\text{A}} \leftarrow \mathbf{\text{A}} - \mathbf{\text{Mem[x]}}$ |
| 0101   | $\mathbf{\text{IN <Device>}}$  | $\mathbf{\text{A}} \leftarrow \mathbf{\text{read from Device}}$           |
| 0110   | $\mathbf{\text{OUT <Device>}}$ | $\mathbf{\text{A}} \leftarrow \mathbf{\text{output to Device}}$           |
| 0111   | $\mathbf{\text{HALT}}$         | $\mathbf{\text{Stop}}$                                                    |
| 1000   | $\mathbf{\text{JMP <x>}}$      | $\mathbf{\text{PC}} \leftarrow \mathbf{\text{x}}$                         |
| 1001   | $\mathbf{\text{SKIPZ}}$        | $\mathbf{\text{If Z=1 Skip next}}$                                        |
| 1010   | $\mathbf{\text{SKIPG}}$        | $\mathbf{\text{If G=1 Skip next}}$                                        |
| 1011   | $\mathbf{\text{SKIPL}}$        | $\mathbf{\text{If L=1 Skip next}}$                                        |
1) Loads the contents of memory location X into A.
	- A stands for Accumulator register
2) Data stored at X is added to A and the sum is stored at A.
3) Stores the contents of A into X.
4) Data stored at X is subtracted to A and the difference is stored at A.
5) A value from the input device is transferred into the AC.
6) Print out the contents of the AC in the output device.
7) Machine stops execution of the program
8) Causes an unconditional branch to address x
9) If the contents of Accumulator=0 then PC=PC+1
10) Condition Codes (GZL)
	- These codes correspond to the output of the ALU unit:
		- G is the Greater than value
		- Z is the zero value
		- L is the Negative value
	- Whichever one is set to 1 corresponds to the output of the ALU unit. and instructs the next execution.
### Program State Word
The PSW is a register in the CPU that provides the OS with information on the status of the running program:
## Assembly Language:
The instruction format of an **accumulator machine** consists of 16 bits:
- 4 bits for the OP code
- 12 bits for the Address
Meanwhile a **load/store architecture** has a **register file** and it has three different instruction formats therefore its assembly will differ to that of the accumulator machine:
- Instruction format 1:
	- Same as accumulator machine:
		- 4 bits for the OP code
		- 12 bits for the Address
- Instruction format 2:
	- 16 bit format:
		- 4 bits for the OP code
		- 4 bits for register $i$
		- 8 bits for the Address
- Instruction format 3:
	- 16 bit format:
		- 4 bits for the OP code
		- 4 bits for register $i$
		- 4 bits for register $j$
		- 4 bits for register $k$
### Assembler:
The assembler translates the Assembly symbolic code to binary machine language.
- **Assembler Directives:**
	- The incorporation of **pseudo-ops** to invoke a special service from the assembler improves the assembly language without generating code:
		1)  **.begin**
			- Tells the assembler where the program starts
		2) .data
			- To reserve a memory 
		3) .end
			- Tells the assembler where to end
