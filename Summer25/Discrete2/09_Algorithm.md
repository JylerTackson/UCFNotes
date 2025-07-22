# Algorithm
Descriptions of an algorithm are equivalent in power to a Turing machines:
- Any clear, unambiguous, and finite set of instructions to a computer, each step of which performs only a finite amount of work.
- By "description" we literally mean an understandable description.

## Church Turing Thesis
Levels of Formality in Discussing Turing Machines
1) Full formal descriptions of the states, alphabets, and transition function of the machine.
2) Quasi-formal implementation descriptions of the way the machine reacts to inputs.
3) Algorithmic high-level descriptions that describe, clearly and unambiguously, an algorithm to be executed.
The Church-Turing Thesis tells us that all three are equivalent!

## Cleanup
Encoding data for Turing machines
- It doesn't matter what encoding we pick; by the Church-Turing Thesis, a Turing machine can use it.
We can refer to an encoded object by enclosing it in angle brackets
- Graph: $G$
- Encoded Graph: $<G>$

![[Pasted image 20250721135524.png]]

## Example
Give an implementation-level description of the following **TM** that decides the following language over the alphabet $\Sigma=\{0,1\}$.
$$L=\{w\;|w\text{ contains an equal number of 0's and 1's}\;\}$$
On input string w:
1) Scan the tape and mark the 1st 0 that has not been marked. If no unmarked 0's are found, got to step 4. Otherwise move the head back to the front of the tape.
2) Scan the tape and mark the 1st 1 that has not been marked. If no unmarked 1's are found, reject.
3) Move the head bac to the front of the tape, go to step 1.
4) Move the head back to the front of the tape, scan for unmarked 1, if found reject, else accept.