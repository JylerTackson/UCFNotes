**Mutual Exclusion** is the main idea of the chapter going over mutually exclusive algorithms that work by reading and writing shared memory. 

# 2.1 Time and Events
In 1687, Isaac Newton wrote, "Absolute, True, and Mathematical Time, of itself, and from its own nature flows equably without relation to any thing external." We endorse his notion of absolute and un-relational because threads share a common time (though not necessarily a common clock). 

A thread is a *state machine*, with state transitions called *events*. 
- Events are *instantaneous:* 
	- They occur at a single instance of time
- Events are **never** *simultaneous*:
	- Distinct events occur at distinct times.

### Helpful Notation:
- Let $a_0$ and $a_1$ be events $s.t. a_0\to a_1$ this can be expressed as an interval $I_A=(a_0,a_1)$ which is the duration between $a_0$ and $a_1$.
- To denote $a_0$ precedes $a_1$, or $a_1$ succeeds $a_0$, we can write $a_0 \to a_1$.

---

# 2.2 Critical Sections
A **critical section** is a block of code that can be executed by only one thread at a time. This property is known as **mutual exclusion**. To implement this property, create a lock class:

```java
public interface Lock {
	public void lock(); // before entering critical section
	public void unlock(); // before leaving critical section
}
```

Threads using the `lock()` and `unlock()` methods must follow a specific format. A thread is well formed if:
1) Every **critical section** is associated with a **Lock object**.
2) The thread calls the `lock()` method when entering.
3) The thread calls the `unlock()` method when leaving.

A thread *acquires* a lock when returning from `lock()` and *un-acquires* a lock when it from the `unlock()` method. While a thread is acquired that lock is *busy*; otherwise, the lock is *free*.

Properties of a `Lock` algorithm:
1) **Mutual exclusion:** One thread holds the lock at any time.
2) **Freedom from deadlock:** If a thread is attempting to acquire or release the lock, then **eventually** some thread acquires or releases the lock.
3) **Freedom from starvation (lockout-freedom):** Every thread that attempts to acquire or release the lock eventually succeeds

---

# 2.3 Two -Thread Solutions
The following are implementations that can be created to solve a lock algorithm for 2 threads and can be scaled to more. Furthermore, each of these threads satisfy the **mutual exclusion** property.

## 2.3.1 `LockOne` Class
This lock is simple, it maintains a boolean flag variable for each thread. To acquire the lock, a thread sets its flag to true and waits until the other thread's flag is false.

Properties:
1) Mutually Exclusive

```Java
class LockOne implements Lock {
	private boolean[] flag = new boolean [2];
	
	public void lock() {
		int i = ThreadID.get();
		int j=1-i;
		flag[i] =true;
		while (flag[j]) {} //wait until flag[j] == false
	}
	
	public void unlock() {
		int i = ThreadID.get();
		flag[i] = false;
	}
}
```


## 2.3.2 `LockTwo` Class
To acquire the lock, a thread sets the `wait` field to **its own ID** and then waits until the other thread changes it. However, by the same reasoning, A must write victim after B, which is a contradiction. 

Properties:
1) Mutually Exclusive

```Java
class LockTwo implements Lock {
	private int victim;
	
	public void lock() {
		int i=ThreadID.get();
		wait = i;
		while(wait == i) {} //wait to acquire thread
	}
	
	public void unlock() {}
}
```

## 2.3.3 `Peterson` Lock Class
We combine the `LockOne` and `LockTwo` algorithms to construct a starvation-free lock algorithm known as the **Petersons Lock**. 

Properties:
1) Mutually Exclusive
2) Starvation Free

```Java
class Peterson implements Lock(){

	private boolean[] flag = new boolean[2];
	
	public void lock(){
		int i = ThreadID.get();
		int j = 1 - i;
		flag[i] = true;
		wait = i;
		while (flag[j] && victim == i) // wait to acquire thread
	}
	
	public void unlock(){
		int i = ThreadID.get()
		flag[i] = false;
	}

}

```

---

# 2.4 Notes on deadlock
In literature, the term *deadlock* is sometimes used more narrowly to refer to the case in which the system enters a **state** from which there is **no way for threads to make progress.** The narrower notion of deadlock is distinguished from **live-lock,** in which two or more threads actively prevent each other from making progress. The definition of dead-lock used in this book [^1]proscribes live-lock as well as the narrower definition defined earlier.

Consider the class definition for LiveLock below, if both threads execute the lock() method, they may indefinitely repeat the following steps:
- Set their respective flag variables to true.
- See that the other thread’s flag is true.
- Set their respective flag variables to false.
- See that the other thread’s flag is false.
Because of this possible live-lock, Live-lock **is not** deadlock-free by our definition.
```Java
Livelock implements Lock {
	private boolean[] flag = new boolean[2];
	
	public void lock() {
		int i = ThreadID.get();
		int j = 1 - i;
		flag[i] = true;
		while(flag[j]) {
			flag[i] = false;
			while (flag[j]) {} //wait
			flag[i] = true;
		}
	}
	
	public void unlock(){
		int i = ThreadID.get();
		flag[i] = false;
	}
	
}
```

---

# 2.5 The filter lock 
The `Filter Lock` generalizes the `Peterson Lock` to work for $n > 2$ threads. It creates $n-1$ "waiting rooms," called `levels`, that a thread must traverse before acquiring the lock. 

Properties:
- Mutual Exclusion
- Starvation-Free
- Deadlock-Free

```Java
class Filter implements Lock {
	
	int[] level;
	int[] wait;
	
	public Filter(int n){
		level = new int[n];
		wait = new int[n];
		
		for(int i = 0 ; i < n ; i++){
			level[i] = 0
		}
	}
	
	public void lock(){
		int me = ThreadID.get();
		for(int i = 1 ; i < n ; i++){
			level[me] = i;
			victim[i] = me;
		}
		
		//Spins while conflicts exists
		while((level[k] >= i && victim[i] == me)) {};
	}

	public void unlock() {
		int me = ThreadID.get();
		level[me] = 0;
	}
}
```

---
# 2.6 Fairness
One caveat about the **starvation-freedom property** is that it **makes no guarantee about how long it make take for the thread to get access to the critical section**.

To define **fairness**, we split the `lock()` method into a ***doorway* section** and a ***waiting* section**, where the doorway section always completes in a bounded number of steps (waiting is unbounded). A section of code that is guaranteed to complete in a bounded number of steps is said to be ***bounded wait-free***.

> [!Definition] Fairness Property
> 
> 

---
# 2.7 Lamport's Bakery Algorithm

---
# 2.8 Bounded timestamps

---
# 2.9 Lower bounds on the number of locations

[^1]: forbid