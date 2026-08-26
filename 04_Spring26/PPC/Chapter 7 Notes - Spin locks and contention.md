
The point of this chapter is to explain how the underlying machine architecture affects the performance of a multi-threading algorithm. We revisit the [[Chapter 1 Notes|mutual exclusion]] problem from chapter 1 aiming at creating protocols. 

A mutual exclusion protocol poses the question: "What do you do if you cannot acquire a lock?". There are two alternatives:
1) If you keep trying, the lock will then be considered a **spin lock**.
2) If you suspend yourself and schedule another task on your thread while the lock is busy, this is considered **blocking**.
Suppose we write a simple concurrent program in which each of the threads repeatedly acquires the Peterson lock. On most modern architectures, the threads finish quickly; alarmingly however, we may discover that the counter's final value may be slightly off from the expected million mark. We discover this because occasionally the threads will be found in the critical section at the same time.

When we proved the `Peterson` lock correct, we relied, without calling attention to it, on the assumption that memory is sequentially consistent. That is, our proof that the `Peterson` lock provides **mutual exclusion** implicitly relied on the assumption that any two memory accesses by the same thread, even to separate variables, take effect in program order.

Unfortunately modern multiprocessors and programming languages typically do not provide sequentially consistent memory nor do they guarantee program order among read and writes.
1) The first culprit are the compilers that reorder instructions to enhance performance. It is possible for the compiler to reorder the order of writes by a thread or if a variable is repeatedly read without being written to, the compiler can choose to eliminate all redundant reads and only keep the first one.
2) The second culprit is the multiprocessor hardware itself. When writing to memory, many multiprocessor architectures writes to a *store buffer* and only writes to a shared memory when needed. This speeds up performance because the hardware does not need to wait for every variable to be written to the shared memory and only writes the needed ones for multiples cores/processors.

# 7.2 Volatile fields and atomic objects
To create a rule, any object field that is accessed by a concurrent thread and is not protected by a critical section will be declared **`volatile`.** Without this declaration, this field will not act like an **Atomic Register:**
