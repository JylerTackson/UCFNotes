**Concurrent Objects** are often best described through their safety and liveness properties, or known as the *correctness* and *progress* properties. 

Three correctness conditions will be examined within the following chapter:
1) **Sequential consistency:** Useful for describing standalone systems.
2) **Linearizability:** Strong condition that supports *composition*
3) **Quiescent consistency:** condition appropriate for applications that require high performance at a cost of placing weak constraints on object behavior.

An example of Concurrently working objects can be threads working utilizing the same lock to enqueue and dequeue items within a a queue. The reason you want to enforce a lock on the critical zone such as enqueue and dequeue here is because if two or more threads are trying to enqueue and dequeue simultaneously, it can cause issues and unexpected behavior with the queue indexing.
![[Pasted image 20260226160147.png]]
In this example, C acquires the lock, observes the queue to be empty and releases the lock. Then B acquires the lock, enqueues b, and releases the lock, Furthermore, then A acquires the lock, enqueues a, and releases the lock. Finally, C re-acquires the lock, dequeues b, and releases the lock.

Unfortunately, it follows from [[Chapter 1 Notes|Amdahl's Law]] that concurrent objects whose methods hold exclusive locks, and there therefore effectively execute one after the other, are less desirable than ones with finer-grained locking or no locks at all. The above implementation is known as method level locking so we are looking for a different solution.

It is easier to reason about the behavior of concurrent objects if we can map their concurrent executions to sequential ones as shown above in the image. This principle is the key to the correctness properties stated above.

# 3.2 Sequential Objects
An object within a programming language can be thought of as a container for data and a set of *methods* which are the only way to manipulate those data. The **API documentation typically says something like the following:** If the object is in such-and-such state before you call the method, then the object will be in some other state when the method returns, and the call will return a particular value, or throw some exception. 

The style of documentation known as **sequential specification** is known as the length of the object's documentation is linear in the number of methods, because each method can be described in isolation. There are a vast number of **potential interactions** among methods, all are characterized succinctly by the methods' side effects on the object state. Finally the object's documentation describes the object state before and after each call, and we can safely ignore any intermediate states that the object may assume.

In a single-threaded program, an object must assume a meaningful state only between method calls. In a multithreaded program, however, overlapping method calls may be in progress at every instant, therefore a **concurrent** object may never be between method calls. If an objects methods can be invoked concurrently by multiple threads, then method calls can overlap in time, and it no longer makes sense to talk about their order.

# 3.3 Sequential consistency

A **method call** is the interval that starts with an ***invocation*** event and continues until the corresponding ***response*** event. Method calls by concurrent threads may overlap, while method calls by a single thread are always sequential. A method call is ***pending*** if its **invocation event** has occurred but is waiting for its **response event** to occur. Furthermore, the order in which a single thread issues method calls is called its ***program order***.

To define ***sequential consistency*** we define what it consists of:
- **Principle 3.3.1:** Method calls should appear to happen in a one-at-a-time sequential order.
- **Principle 3.3.2:** Method calls should appear to take effect in program order.

## 3.3.1 Sequential consistency versus real-time order
In a scenario where you have multiple threads working with the same sequential object, when one operation completes before another begins, we say that the first operation precedes the second in the ***real-time order***. Furthermore, if the threads are doing work that are completely unrelated, we are able to say that *sequential consistency* is free to re-order them. There are scenarios in which you must be careful, or it is considered unacceptable, to reorder method calls based on sequential consistency.

## 3.3.2 Sequential consistency in nonblocking
Sequential consistency **NEVER** requires one method call to block waiting for another to complete. For any pending method call in a sequentially consistent concurrent execution, there is some sequentially consistent response, that is, a response to the invocation that could be given **immediately** without violating sequential consistency. We say that a correctness condition with this property is *nonblocking*, therefore Sequential consistency is *nonblocking.*

## 3.3.3 Compositionality
A correctness property $\mathcal{P}$ is *compositional* if:
- whenever each object in the system satisfies $\mathcal{P}$, the system as a whole satisfies $\mathcal{P}$.
**Compositionality** is important because it enables a system to be assembled easily from **independently derived components**. This is important because any sufficiently complex and scalable system must be designed and implemented in a ***modular* fashion.** *Sequential consistency* is **NOT** compositional, the sequentially consistent execution as a whole of multiple threads is **not** sequentially consistent.

# 3.4 Linearizability
Sequential consistency has a serious drawback:
