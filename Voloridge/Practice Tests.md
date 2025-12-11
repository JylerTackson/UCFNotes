Write a fetch() call that retrieves all orders for a customer using query parameters
`customerId` and optional status, including a bearer token
```js
async function retrieveOrders(customerId, status){
	//prepare arguments
	const parameters = {customerID, status}
	//prepare URL
	const url = `https://fictionalURL/asdfasdf/?${JSON.stringify(parameters)}`
	
	try{
		const response = await fetch(url)
		
		//validate response
		if(!response.ok){
			throw new Error("response was not ok")
		}
		
		//parse response
		const parse = await JSON.stringify(response)
		return parse
	}catch(err){
		console.log(err)
	}
	
}
```

The above is incorrect because I did not create the options for the `GET` request to include the bearer token. The bearer token is to allow the server to check for authorization for the user. While the options of fetch request have three main components, when you do a `GET` or `HEAD` request you leave out the `body` since you are not affecting the server state by sending it and information.

`Content-Type` is used when sending information while `Accept` is used to tell the server what we are willing to receive back. `Authorization` is used to tell the server what our auth is.

```js
//create our parameters, normall passed into the function
const parameters = {
	customerID: "123",
	status: "OPEN"
}
//prepare the url
const url = `https://api.example.com/orders?${params.toString()}`
//create the options for fetch
const options = {
	method: "GET",
	headers: {
		"Authorization": "Bearer YOUR_TOKEN_HERE",
		"Accept": "application/json" 
	}
}

try{
	const response = await fetch(url, options)
	
	if(!response.ok){
		throw new Error("response not ok")
	}
	
	const parsed = await JSON.stringify(response)
	return parsed
}catch(err){
	console.log("Error", err)
}
```

---

Write a Python class `Vector2D` with attributes `x` and `y`, a `magnitude()` method, and an overloaded `__add__()` operator

```python
import math

class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def magnitude(self):
        return math.sqrt(self.x**2 + self.y**2)

    def __add__(self, other):
        return Vector2D(self.x + other.x, self.y + other.y)
```
---
**Explain composition vs. inheritance and when each is preferable.**
- Inheritance creates an “is-a” relationship where a subclass reuses and extends a base
class (e.g., Car is a Vehicle). Composition creates a “has-a” relationship by building
classes out of other objects (e.g., Car has an Engine).

---

Identify and correct the bug in:
```python
def compute(values=[]):
	values.append(10)
	return values
```
Avoid using a mutable default, you should set values to None in the parameter and then do a check to see if it is none, then set it to an empty list

---
Implement a factory pattern returning either a Car or Boat object depending on input.

---

Given:
```
class A:
def foo(self): return "A"
class B(A):
def foo(self): return "B"
```
Describe what is printed by:
```
x = A()
y = B()
print(x.foo(), y.foo())
```

Show how to use a context manager to open and read all lines in a file.
Define duck typing in Python and provide an example.
State the amortized time complexity of list.append() and explain why.
Write a generator function yielding squares from 0 to n.
Explain why immutability (e.g., tuple) is beneficial for hashing or concurrency.