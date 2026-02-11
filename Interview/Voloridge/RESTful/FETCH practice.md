A backend exposes the endpoint:
```python
GET https://api.volo-test.com/users
```
Write a `fetch` request that retrieves all users and logs them to the console as JSON.

This is a very simple get function, you are provided the URI and apply that to the fetch parameter. Once we have the response from the fetch we then scan for proper response and then JSON it.

```javascript
async function getUsers(){
	try{
		const response = await fetch(https://api.volo-test.com/users)
		
		if(!response.ok){
			throw new Error("response not ok")
		}
		
		const users = await response.json();
		console.log(users)
	} catch(error){
		console.error("Error: ", error)
	}
}
```

---

You are given the endpoint:
```python
GET https://api.volo-test.com/users?active=true&limit=10
```
Write a function `getActiveUsers()` that returns the parsed JSON array.

```js
async function getActiveUsers(){
	const params = new URLparams({
		active: true,
		limit: 10
	})
	
	const url = `https://api.volo-test.com/users?${params.toString()}`

	try{
		const response = await fetch(url)
		
		if(!response.ok){
			throw new Error("response not ok")
		}
	
		const parsed = await response.json()
		return parsed;
	} catch(Error){
		console.log("Error", Error)
	}

}
```

---

Endpoint:
```python
GET https://api.volo-test.com/profile/:id
```
Write a function `fetchProfile(id)` that:

1. Performs the GET request
2. Throws an error if the response status is not 200
3. Returns the parsed JSON on success.

```js
async function fetchProfile(id){
	const url = `https://api.volo-test.com/profile/:${id}`
	
	try{
		const response = await fetch(url);
		
		if(response.status != 200){
			throw new Error("Response NOT 200")
		}
		
		const parsed = await response.json();
		return parsed;
	}catch(err){
		console.log("Error", err)
	}
}
```

---

Backend:
```python
POST https://api.volo-test.com/users 
Content-Type: application/json 
Body: { "name": string, "email": string }
```
Write a function `createUser(name, email)` that sends the required POST request and returns the created user object.

```js
async function createUser(name, email){
	//Construct the URL
	const url = `https://api.volo-test.com/users`
	
	//Construct Message to the Server
	const payload = { name, email }
	const options = {
		method: "POST",
		headers: {
			"Content-Type": "application/json"
		},
		body: JSON.stringify(payload)
	}
	
	try{
		const response = await fetch(url, options).
	
		if(!response.ok){
			throw new Error("Response Not OK")
		}
	
		const parsed = await response.json()
		return parsed;
	}catch(err){
		console.log("Error", err)
	}
}
```

---

An endpoint:

```js
POST https://api.volo-test.com/orders
```

Write code to:
- Submit a new order `{ productId, quantity }`
- Check specifically for a `201` status
- Throw an error if not 201

```js
async function newOrder(productID, quantity){
//construct URL
const url = `https://api.volo-test.com/orders`

//construct Message
const payload = { poductID, quantity }
const options = {
	method: "POST",
	headers: {
		"Content-Type": "application/json"
	},
	body: JSON.stringify(payload)
}

try{
	const response = await fetch(url, options)
	
	if(response.status != 201){
		throw new ERROR("Stauts was not 201")
	}
	
	const parsed = await response.JSON()
	return parsed;
}catch(err){
	console.log("ERROR", err)
}

}
```

---


Endpoint:
```js
PUT https://api.volo-test.com/users/:id
```
The request body:
```js
{   "email": "newEmail@example.com" }
```
Write `updateEmail(id, newEmail)` using `fetch` and return the updated object.

```js
async function updateEmail(id, newEmail){
	//prepare URL
	const url = `https://api.volo-test.com/users/:${id}`

	//prepare options
	const payload = {id, newEmail}
	const options = {
		method: "PUT",
		headers: {
			"Content-Type": "application-json"
		},
		body: JSON.stringify(payload)
	}

	try{
		const response = await fetch(url, options)
		
		if(!response.ok){
			throw new ERROR("Response was not OK")
		}
		
		const parsed = await response.JSON()
		return parsed;
	}catch(err){
		console.log("ERROR", err)
	}

}
```

---

Backend:
```js
PATCH https://api.volo-test.com/settings
```
Body fields are optional:
```
{   "theme": "dark" | "light",   "notifications": boolean }
```
Write a function `updateSettings(options)` that sends the PATCH request with only the provided fields.

```js
async function updateSettings(options){
	//prepare URL
	const url = `https://api.volo-test.com/settings`
	//prepare options
	const options = {
		method: "PATCH",
		headers: {
			"Content-Type": "application/json"
		},
		body: JSON.stringify(options)
	}
	
	try{
		const response = await fetch(url, options)
		
		if(!response.ok){
			throw new Error("Error")
		}
		
		const parsed = await response.JSON();
		return parsed;
	}catch(err){
		console.log("ERROR", err)
	}
}
```
