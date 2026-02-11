In regards to finding all the prime numbers between 1 and $10^n$, a promising way to split the work among the threads is to assign each thread one integer at a time. When a thread is finished testing an integer, it asks for another. To this end, we introduce a *shared counter*, an object that encapsulates an integer value, and that provides a `getAndIncrement()` method, which increments the counter's value and returns the counter's prior value.

```Java
public class Counter{
	private long value;
	public Counter(long i){
		this.value = i;
	}
	public long getAndIncrement(){
		return this.value++;
	}
}
```

This works on a single thread however when you include multiple threads it stops working. It stops working because the above code is in effect an abbreviation of the following:
```Java
long temp = value;
value = temp + 1;
return temp;
```
In this code above, value is a field of the Counter object which is shared among all the threads, however each thread has its own copy of temp which is a local variable. 
Some hypothetical issues:
1) Assuming that that both thread 1 and 2 set their temp variable equal to the value variable of the Counter class at the same time, they will both return the same thing to the value variable which will not Increment it.
You must decide on which side to pass each thread using a shared counter, who goes first and who goes second.

**Speedup**: ratio between the time it takes on processor to complete the job versus the time it takes $n$ concurrent processes to complete the same job.
$$
S=1-p+\frac{p}{n}
$$
**Amdahl's law:** captures the notion that the extent to which we can speed up any complex job is limited by how much of the job must be executed sequentially. However using amdahl's law, we can assume that the maximum speedup is:
$$
S=\frac{1}{1-p+\frac{p}{n}}
$$

