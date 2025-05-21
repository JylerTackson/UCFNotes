# General Semantics - Calls & Returns
The subprogram **Call and Return** operations of a language are together called its **subprogram linkage.** A subprogram call has **numerous actions** associated with it:
- Parameter passing
- Static local variables
- Execution status of calling program
- Transfer of control
- Subprogram nesting

# Simple Subprograms
## Call Semantics
A simple subprogram has the following semantics in order for it to execute:
1) Save the execution status of the caller
2) Carry out the parameter-passing process
3) Pass the return address to the caller
4) Transfer control to the caller
## Return Semantics
If **pass-by-value parameters are used** then move the current values of those parameters to the corresponding actual parameters. If it is a **function**, move the functional value to a place the caller can get it. Finally restore the execution status of the caller and transfer control back to the caller.
## Parts
There are two separate parts within a simple subprogram:
- Actual Code
- Non code - local variables and data
	- The format, or layout, of the an executing subprogram is called an *activation record.*
		- An *activation record instance* is a collection of data for a particular subprogram activation.
# Subprograms with Stack-Dynamic Local Var's



# Nested Subprograms

# Blocks

# Dynamic Scoping