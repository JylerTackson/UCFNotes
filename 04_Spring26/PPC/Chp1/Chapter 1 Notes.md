**Moores Law:** The number of transistors on a microchip doubles approximately every two years, resulting in exponentially increased computing power at lower costs.

As Moore's law approached its 50-year anniversary, many manufacturers turned to "multicore" architectures, in which multiple processors (cores) on a single chip communicate directly though hardware **caches**. This book focuses on on how to program multiprocessors that communicate via a shared memory, shared-memory multiprocessors are often called, multicores. We approach multiprocessor programming from two directions:
1) **Principles:**
	- Within the principles section of the book, you want to focus on **computability:** figuring out what can be computed in an asynchronous concurrent environment.
		- **Program Correctness:** The specification and verification of what a given program actually does. The correctness of multiprocessor programs is more complex than that of their sequential counterparts. **Sequential correctness** is mostly concerned with safety properties such as a traffic light in the situation power fails. **Concurrent Correctness** encompasses a variety of *liveness* properties that have no counterparts in the sequential world. 
			- A *liveness* property states that a particular good thing will happen, e.x. a red traffic light turning green.
2) **Practice:**
	- Within the practice section of the book, you want to focus on **performance:** Analyzing the performance of multiprocessor algorithms is different from sequential algorithms in the since that **sequential algorithms** are based off of well-established and well-understood abstractions. **Multiprocessor algorithms** require programs that would sometimes seem bizarre to someone unfamiliar with multiprocessor architectures due to trying to optimize the underlying memory of the processors. 


# 1.1 Shared Objects and Synchronization
This sections speaks about the timing issues with reading and writing between variables stored in local memory between multiple threads. In **Chapter 5**, we discuss how modern multiprocessor hardware provides a special *read-modify-write* instruction set that allows these threads to read, modify, and write a value to memory in one *atomic* hardware step.
- **Atomic Hardware Step:** an indivisible CPU operation that completes entirely without interruption, ensuring data integrity in parallel processing.
Furthermore, this atomic behavior can be ensured by guaranteeing in software that only one thread executes the read-and-write sequence at a time.

This is called the **mutual exclusion problem**: a classic coordination problem in multiprocessor programming is the problem of ensuring that only one thread can execute a particular block of code at a time.