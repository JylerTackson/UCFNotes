**Moores Law:** The number of transistors on a microchip doubles approximately every two years, resulting in exponentially increased computing power at lower costs.

As Moore's law approached its 50-year anniversary, many manufacturers turned to "multicore" architectures, in which multiple processors (cores) on a single chip communicate directly though hardware **caches**. This book focuses on on how to program multiprocessors that communicate via a shared memory, shared-memory multiprocessors are often called, multicores. We approach multiprocessor programming from two directions:
1) **Principles:**
	- Within the principles section of the book, you want to focus on **computability:** figuring out what can be computed in an asynchronous concurrent environment.
		- **Program Correctness:** The specification and verification of what a given program actually does. The correctness of multiprocessor programs is more complex than that of their sequential counterparts. **Sequential correctness** is mostly concerned with safety properties such as a traffic light in the situation power fails. **Concurrent Correctness** encompasses a variety of *liveness* properties that have no counterparts in the sequential world. 
			- A *liveness* property states that a particular good thing will happen, e.x. a red traffic light turning green.
2) **Practice:**
	- Within the practice section of the book, you want to focus on **performance:** Analyzing the performance of multiprocessor algorithms is different from sequential algorithms in the since that **sequential algorithms** are based off of well-established and well-understood abstractions. **Multiprocessor algorithms** require programs that would sometimes seem bizarre to someone unfamiliar with multiprocessor architectures due to trying to optimize the underlying memory of the processors. 

---

# 1.1 Shared Objects and Synchronization
This sections speaks about the timing issues with reading and writing between variables stored in local memory between multiple threads. In **Chapter 5**, we discuss how modern multiprocessor hardware provides a special *read-modify-write* instruction set that allows these threads to read, modify, and write a value to memory in one *atomic* hardware step.
- **Atomic Hardware Step:** an indivisible CPU operation that completes entirely without interruption, ensuring data integrity in parallel processing.
Furthermore, this atomic behavior can be ensured by guaranteeing in software that only one thread executes the read-and-write sequence at a time.

This is called the **mutual exclusion problem**: a classic coordination problem in multiprocessor programming is the problem of ensuring that only one thread can execute a particular block of code at a time.

---
# 1.2 Fable
This section breaks down a fundamental problem to better explain how threads share resources, this problem is better known as as *coordination problem* between threads (or just *protocol*).

This section reviews the **flag protocol:**
- If `flag` is `false`, the process sets it to `true` and enters.
- If `flag` is `true`, the process waits.
- When leaving, the process sets `flag = false`.
	- This is a software approach of solving the mutual exclusion problem.
## 1.2.1 Properties of a mutual exclusion protocol
1) **Mutual Exclusion** property:
	- The property that states only a single thread can execute a particular block of code at a time.
		- This is a **safety property**.
2) **Deadlock-Freedom** property:
	- The property that states only one thread wants to execute a specific block of code, then it eventually succeeds. Furthermore, if more than one thread wants to execute the code of block, then eventually at least one of them succeeds.
		- This is a **liveness property**.
3) **Starvation-Freedom** property (aka *lockout-freedom*):
	- If a process requests access to a critical section, it will eventually enter it; meaning no process can be postponed forever and wait time is finite.
4) **Waiting** property:
	- It is explained that the mutual exclusion problem **requires waiting** however it can be solved without waiting in many other coordination problems. 

## 1.2.2 The moral
Two kinds of communication occur natural in concurrent systems:
1) **Transient:** communication that requires both parties to participate at the same time.
2) **Persistent:** communication that allows the sender and receiver to participate at different times.

The *mutual exclusion* problem request persistent communication, furthermore **interrupts** are a common communication protocol in concurrent systems used for threads to get the attention of one another. 

---

# 1.3 The Producer-Consumer Problem

The **producer–consumer problem** is a synchronization problem involving two types of threads that share a buffer:

- The **producer** generates data and places it into a shared buffer.
- The **consumer** removes data from that buffer and processes it.

The main goal in the P-C problem is to coordinate access s.t:
1. The producer does not add data to a full buffer.
2. The consumer does not remove data from an empty buffer.
3. The shared buffer is accessed safely (mutual exclusion).

A simple conceptual version using shared state:
- The producer:
    - Waits if the buffer is **full**
    - Produces an item
    - Marks the buffer as **non-empty**
        
- The consumer:
    - Waits if the buffer is **empty**
    - Removes an item
    - Marks the buffer as **non-full**

### Properties of P-C Problem:
1) **Mutual Exclusion** property: The Producer and Consumer threads are never in the critical zone together.
2) **Starvation-Freedom** property: If a process requests access to a critical section, it will eventually enter it; meaning no process can be postponed forever and wait time is finite.
3) **Producer-Consumer** property: The consumer relies on the producer to provide it with data within the buffer, furthermore the producer relies on the consumer to empty the buffer so it can create more data.

---
# 1.4 Readers-Writers Problem

The Readers-Writers problem consists of a/some thread(s) that are reading and some that are writing to shared memory and we must devise a coordination protocol to properly read and write to the shared memory to share the full message between the threads. In the context of shared-memory multiprocessors, a solution to the readers–writers problem is a way of allowing a thread to capture an instantaneous view of several memory locations. Capturing such a view without waiting, that is, without preventing other threads from modifying these locations while they are being read, is a powerful tool that can be used for backups, debugging, and in many other situations. Surprisingly, the readers–writers problem does have solutions that do not require waiting.

---
# 1.5 & 1.6 Parallel Programming

When upgrading from a uniprocessor to an *n-way* processor, in an ideal world, it should be an *n-fold* increase in computational power. However in practice, this almost never happens. The primary reason is that most real-world computational problems cannot be effectively parallelized without incurring costs from commination and coordination of threads. 

**Amdahl's law:** the extent to which we can speed up any complex job is limited by how much of the job must be executed sequentially.
- **$S\to$** *speedup* of a job
	- Ratio between:
		- Time it takes one processor to complete the job
		- Time it takes *n* concurrent processors to complete the same job.
- **$p\to$** fraction of the job that can be executed in parallel

*Amdahl's law* states that the maximum speedup, that is, the ration between the sequential (single-processor) time and the parallel time is:
$$
\begin{equation}
\tag{Amdahl's Law}
S=\frac{1}{1-p+\frac{p}{n}}
\end{equation}$$

