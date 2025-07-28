### Traps:
All interrupts associated with program errors or instructions involving malicious program actions are traps.

### I/O Interrupt
This type of interrupt occurs when an I/O device sends a signal to inform the CPU that an I/O operation has been completed. The I/O flag is used in the PSW to assert this type of interrupt. When an I/O interrupt occurs, the program state of the running program is saved; thus, it can be restarted from the same point where it left off once the I/O interrupt has been handled.


### Timer Interrupt
When a CPU has several programs running, processor sharing is required to allow each program to use the CPU for a certain amount of time. Once the time is allotted to a running program a **Timer Interrupt** is thrown to change priority to a different program. To implement the timer interrupt, we need to add:
- CPU Register called **Timer**
- Flag called **Timer Interrupt Flag** (TI)

Works this way:
- The Timer register is set to a specific value depending on how long we want to run the program
- The timer register is decremented by one at each clock tick received by the CPU.
- When the timer reaches zero, TI flag is set to 1.


### System Call
The mechanism used to request services from the supervisor is known as a system call or supervisor call (SVC). A system call is an instruction that triggers a software interrupt, and the format of the system call instructions (in a tiny VM/0) is:
$$SVC \;B,<index>$$


#### Types of Interrupts

Software Interrupts:
- These interrupts are synchronous and occur when a program is executing an instruction in the CPU.
	1) System calls (SVC)
	2) Traps

Hardware Interrupts:
- These interrupts are asynchronous and could be triggered at any moment during the Instruction Cycle.
	1) Timer Interrupt
	2) I/O Interrupt