# Introduction
The ISA of the PM/0 has three components:
- OP - code
- L - Lexicographical code
- M - Multiple meanings depending on op code
	- A number when OP is LIT or INC
	- A program address when OP is JMP, JPC, or CAL
	- A data address when OP is LOD, STO
	- The identity of the operation associated to the OPR op-code.
		- OPR 0 2 (ADD)
		- OPR 0 4 (MUL)
- THe list of instructions can be found below 
	- Appendix A
	- Appendix B


---
# Appendix A - ISA
In the following tables

| Index: | Example: | Explanation:                                                                                                                                           |
| ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 01     | INC 0,M  | Allocate **M** memory words (increment SP by M). First three are reserved to Static Link **(SL)**, Dynamic Link **(DL)**, and Return Address **(RA)**. |
| 02     | OPR 0,M  | Operation to be performed on the data at the top of the stack (or return from function).                                                               |
| 03     | LOD L,M  | Load value to top of stack from the stack location at offset **M** from **L** lexicographical levels down.                                             |
| 04     | STO L,M  | Store value at top of stack in the stack location at offset **M** from **L** lexicographical levels down                                               |
| 05     | CAL L,M  | Call procedure at code index **M** (generates new Activation Record and PC $\leftarrow$ M)                                                             |
| 06     | LIT 0,M  | Pushes a constant value M onto the stack                                                                                                               |
| 07     | JMP 0,M  | Jump to instauction M                                                                                                                                  |
| 08     | JPC 0,M  | Jump to instruction M if top stack element is 0                                                                                                        |
| 09 - 1 | SYS 0,1  | Write the top stack element to the screen                                                                                                              |
| 09 - 2 | SYS 0,2  | Read in input from the user and store it on top of the stack                                                                                           |
| 09 - 3 | SYS 0,3  | End of program (Set "eop" flag to zero)                                                                                                                |



| OP Code Number | Op Mnemonic | L   | M   | Explanation                                                                                                                                                       |
| -------------- | ----------- | --- | --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 01             | INC         | O   | n   | Allocate n locals on the stack: $$sp\leftarrow sp-n$$                                                                                                             |
| 02             | RTN         | O   | O   | Returns from a subroutine is encoded 000 and restores the caller's AR: $$sp\leftarrow bp+1;bp\leftarrow pas[sp-2];pc\leftarrow pas[sp-3]$$                        |
| 03             | LOD         | n   | a   | Load value to top of stack from the stack location at offset $o$ from $n$ lexicographical levels down: $$sp\leftarrow sp-1;pas[sp] \leftarrow pas[base(bp,n)-o]$$ |
| 04             | STO         | n   | o   | Store value at top of stack in the stack location at offset $o$ from $n$ lexicographical levels down:$$pas[base(bp,n)-o]\leftarrow pas[sp];sp=sp+1$$              |
| 05             | CAL         | n   | a   | Call the procedure at code address $a$, generating a new activation record and setting PC to $a$:                                                                 |
| 06             | LIT         | O   | n   | Literal push                                                                                                                                                      |
| 07             | JMP         | O   | a   | Jump to address $a$                                                                                                                                               |
| 08             | JPC         | O   | a   | Jump conditionally: if the value in stack\[sp\] is 0, then jump to $a$ and pop the stack:                                                                         |
| 09             | SYS         | O   | 1   | Output of the value in stack\[SP\] to standard output as a character and pop                                                                                      |
|                | SYS         | O   | 2   | Read an integer, as character value, from standard input and store it on the top of the stack.                                                                    |
|                | SYS         | O   | 3   | Hal the program (Set "eop" flag to zero)                                                                                                                          |

---
# Appendix B - Arithmetic/Logical Instructions

| OPR 0,# | Instruction |
| ------- | ----------- |
| 0,1     | ADD         |
| 0,2     | SUB         |
| 0,3     | MUL         |
| 0,4     | DIV         |
| 0,5     | EQL         |
| 0,6     | NEQ         |
| 0,7     | LSS         |
| 0,8     | LEQ         |
| 0,9     | GTR         |
| 0,10    | GEQ         |

---
# Appendix C - Execution
For every line of input there are 3 values representing the three values shown in the [[HW1 - SPECS#Introduction]] of the assignment:
1) Op code
2) Lexicographical code
3) Operation depending on opcode

The initial CPU register values in this appendix are:
- **SP = 500**
	- Stack Pointer - Points to the top of the stack.
- **BP = $\mathbf{SP-1}$**
	- Base Pointer - Points to the base of the current Activation Record.
- **PC=10**
	- Program counter - a register/pointer that points to the next instruction to be executed.
- **IR=0 0 0**
	- Instruction register - A register that stores the instruction to be executed by the process.


---
# NOTES:
1) We are working at the CPU level therefore the instruction format **must have only 3 fields**. Any program whose number of fields in the instruction format is greater that 3 will get a zero.

2) If your program does not follow the specifications, your grade will get a zero.

3) If any of the instructions is implemented by calling a function your grade will be a zero.

4) If you use DMA, you will get a zero.

5) Pointers are not allowed, except when reading a file.
---
# Simplified Op-Code List:
## Basic Instructions
01 – LIT   (Load literal into register)
02 – RTN   (Return from subroutine)
03 – LOD   (Load from stack to register)
04 – STO   (Store from register to stack)
05 – CAL   (Call procedure)
06 – INC   (Increment stack pointer)
07 – JMP   (Jump)
08 – JPC   (Jump conditional)
09 – SIO 1 (Output)
10 – SIO 2 (Input)
11 – SIO 3 (Halt)

## Arithmetic & Operations
12 – NEG   (Negate)
13 – ADD   (Add)
14 – SUB   (Subtract)
15 – MUL   (Multiply)
16 – DIV   (Divide)
17 – ODD   (Check odd)
18 – MOD   (Modulo)
19 – EQL   (Equal)
20 – NEQ   (Not equal)
21 – LSS   (Less than)
22 – LEQ   (Less than or equal)
23 – GTR   (Greater than)
24 – GEQ   (Greater than or equal)