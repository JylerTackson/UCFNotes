
## Translating Assembly Language to Object Code
**Assemblers** are programs that translate assembly language into an executable version of the program.
To program a computer in assembly the programmer needs a basic knowledge of computer organization, we will describe the different components of a hypothetical **one address** tiny computer.
- The computer has a process with three registers:
	- (A) The accumulator for data values
	- (PC) Program Counter which points to the next instruction
	- (IR) Instruction Register which holds the instruction.
- All IO devices are connected to the accumulator
- Computer has main memory (RAM), we refer to it as MEM
- Instruction format consists of two fields
	- Opcode $\rightarrow$ Tells the computer the action to be carried out
	- Operand $\rightarrow$ This field identifies a $<\text{memory address}>$ or a $<\text{device number}>$.

---
### ISA of the tiny computer
1) 01-LOAD $<X>$
	- Loads the contents of memory location X into A
2) 02-ADD $<X>$
	- The data value stored at address X is added to the A register, and the result is stored back in A.
3) 03-STORE $<X>$
	- Store the contexts of the A register into memory location X.
4) 04-SUB $<X>$
	- Subtracts the value located at address X from the value stored in A, stores the result back in A.
5) 05-IN $<Device\#>$
	- A value from the input device is transferred into A.
6) 06-OUT$<Device\#>$
	- Print out the contents of A in the output device
		- Device #5 - Keyboard
		- Device #7 - Printer
		- Device #9 - Screen
7) 07-HALT
	- The machine stops execution, control returns to the OS
8) 08-JMP$<X>$
	- Causes an unconditional branch to address X. $PC \leftarrow X$ 
9) 09-SKIPZ
	- If the contents of A=0, next instruction is skipped.

---
### Object Code
![[Pasted image 20250721225608.png]]
Shown above is an example of the **Assembler** translating **Assembly $\to$ Object Code**.
#### Object File Format
The object File Format has more than just data and text sections, there are several sections within the object file format:
- **Header**: In the header we will find information about all sections within the file; for example, program name or id. In addition, the header has the starting address and length for each section within the file.
- **Text Section**: Executable instruction.
- **Data Section**: Data.
- **Relocation section**: Addresses to be fixed by the loaded and/or linker.
- **Symbol table section**: Global symbols (labels) in the program
- **Debugging section**: Source file and line number information and the description of the data structures.
#### **Object Code:**
- Shown on the bottom right hand side is the translation of the Assembly code provided into Object code. This is done by referring to the **Opcode table** in the top right which allows us to transfer each instruction into its binary representation. For example:
	- The instruction   ADD$\;\to\;$ 0010, furthermore, attached to the add is the address which is expressed as a decimal number, this is then transferred to binary with the binary instruction appended to the front resulting in:
		- $\text{ADD}\;<001> \; \Rightarrow \;0001\;0000\;0000\;0001$

---
### Assembler Directives
These pseudo-operations do not generate code however they direct the assembler and help create a more functional program:
- **.begin** $\rightarrow$ tells the assembler where the program instructions begin
- **.data** $\to$ tells the assembler to reserve a memory location
- .end $\rightarrow$ tells the assembler where the program ends

### Labels
Labels are symbolic names used to identify memory locations (variables).
![[Pasted image 20250722154039.png]]

### Assembler Passes
#### $1^{\text{st}}$ Pass - Symbol Table
In the first pass the assembler scans the program line by line identifying labels and creating a **symbol table** by associating labels with their associated memory address.

Shown above in the image, the symbol table correlates the provided labels with the address on the right side of the assembly code.

#### $2^{\text{nd}}$ Pass - Object Code
As described above, in the second pass, the assembler then generates **object code**.
However, now that we have a **Symbol Table**, the translation is done by replacing each opcode with its binary representation (as before), then using the symbol table addresses it calculates the instruction addresses as PC-relative addresses.



---
### Static Linking




---
### Loader
The object code, also known as the executable file, is stored in the hard drive and to execute this we need a program called the **Loader**. These programs load from the hard drive into MEM for execution. Loaders were a significant step because they are capable of loading programs into memory for execution. Without loaders the programs would manually load one instruction after another in binary.

The executable shown above is the `a.out` format for early version of `UNIX` systems however, executable formats are more elaborate, such as the one used in hw4:
- **(`elf`) Executable and Linkable Format**
	- Object code format used on modern Linux system

#### Absolute loaders
An Absolute loader is able to load an object in a specific memory location. In early computing days, the the programmer was responsible for including the absolute address in the directive `.begin` or `.orig`. The program in the translation process was contained in a single object file, and the file was loaded in memory as a monolithic entity. The steps taken by the absolute loader are as follows:

1) The header record is checked to verify the correct program has been presented for loading
2) The loader will load the program at the memory location defined in the object code by the programmer.
3) Each text record is read and placed at the indicated address.
4) Each data record is read and moved to the indicated memory address. All data is placed right after text.
5) When the `.end` record (`EOF`) is encountered, the loader passes on control to the user program by jumping to the specified address to being execution.


