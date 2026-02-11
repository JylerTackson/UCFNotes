RESTful API is an interface that two computer systems use to exchange information securely over the internet. There are two aspects to this, Representation State Transfer (REST) and the application programming interface (API).

---
### REST
Representation State Transfer (REST) is a software architecture that imposes conditions on how an API should work. The term RESTful API generally refers to web API's, furthermore you can use REST and RESTful interchangeably.

### API
An application programming interface (API) defines the rules that you must follow to communicate with another software system. Developers expose and create an API so that applications can communicate programmatically.

### How does a RESTful API work?
These are the general steps for any REST API call:
1. The client sends a request to the server. The client follows the API documentation to format the request in a way that the server understands.
2. The server authenticates the client and confirms that the client has the right to make that request.
3. The server receives the request and processes it internally.
4. The server returns a response to the client. The response contains information that tells the client whether the request was successful. The response also includes any information that the client requested.
---
### URI & URL
For REST services, the server typically performs resource identification by using a Uniform Resource Locator (URL).

**Common HTTP Methods**
- **GET**
	- Used to access resources that are located at a specified URL.
- **POST**
	- Used to send data to the server.
- **PUT**
	- Update an existing resource on the server.
- **DELETE**
	- Used to delete an resource on the server.
- **PATCH**
	- Used to **partially** update an existing resource on the server.
- **HEAD**
	- Used to access resources but **only returns headers**.

---
### RESTful Server Response
There are three main aspects to a server response:

##### 1) Status Line:
The status line contains a three-digit status code that communicates the status of the request
- **2XX:** Indicates success
	- **200**: Generic success
	- **201**: Created - *POST*
	- **202**: Accepted - *async processing*
	- **204**: No Content - *DELETE or UPDATE*
- **3XX:** Indicates URL redirection
	- **301**: Moved Permanently
	- **304**: Not Modified - *caching*
- **4XX & 5XX:** Indicates Errors
	- **400**: Bad Request
	- **401**: Unauthorized - *missing/invalid credentials*
	- **403:** Forbidden - *client authenticated but not allowed*
	- **404**: Not Found
	- **409**: Conflict - *version conflict*
	- **429**: Too Many Requests - *rate limiting*
	- **500**: Internal Server Error
	- **503**: Service Unavailable

##### Message Body
The response body contains the resource representation. Clients can request information in XML or JSON formats, which define how the data is written.

##### Headers
The response also contains headers or metadata about the response. They give more context about the response and include information such as the **server, encoding, date,** and **content type**.
- **Content-Type:**
	- Specifies the **format of the data being sent**.
- **Accept:**
	- Tells the server which **response formats** the client is willing to accept.
- **Authorization:**
	- Provides the client's credentials or tokens.
- **If-Modified-Since:**
	- Instructs the server to return the resource only if it has been updated after the specified timestamp
- **If-None-Match:**
	- Tells the server to return the resource only if its ETag does not match the provided value, preventing unnecessary data transfer when nothing has changed.