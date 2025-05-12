# What is System Software?
A System Software consists of a set of programs that support the operation of a computer system.
- They help the programmer simplify the programming process.
- Create an environment to run application software efficiently.
	- Program Development Environment:
		- Text Editor
		- Compiler
		- Assembler
		- Linker
		- Debugger
	- Run-Time Environment:
		- Loader
		- Libraries
		- Dynamic Linker
		- Operating System
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
- **Instruction Register (IR):** A register stores the instruction to be executed by the process
- **Decoder:** a circuit that decides which instruction the processor will execute. Takes instruction op-code from the **IR** as input and outputs a signal to the Control Unit to carry out the execution.
- **Accumulator (A):** the only register that can be used by user programs.
## A program of an isolated system:

**Fetch - Execute Cycle:** In the VN machine the instruction Cycle is defined by the following loop:
-  **Data Movement 1:** The transfer of the contents from **PC** into **MAR.**
	- $\mathbf{\text{MAR}} \leftarrow \mathbf{\text{PC}}$
- **Data Movement 2:** The transfer from a memory location **(MAR)** into the register **(MDR)**. The address of the memory location has been stored previously into the **MAR** register.
	- $\mathbf{\text{MDR}} \leftarrow \mathbf{\text{MEM[MAR]}}$
-  **Data Movement 2.1:** The transfer from a memory location 
## The Instruction Format:

## Assemble Language: