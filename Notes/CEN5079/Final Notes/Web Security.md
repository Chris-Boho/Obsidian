
### What is Web Security?
- Detection:
	- web app unintended behavior
	- user behavior diverges from normal
	- logging
- Prevention:
	- reduce attack surface
	- minimize the chance of data leakage
- Respond:
	- moving target defense
- Client Application Security
	- Prevent users from being attacked while using web apps
	- from social engineering
	- from trackers
- Server Application Security
	- attackers can run arbitrary code, send anything to server

### Why is Web Security Hard?
- ambitious goal: run untrusted code securely
- low level access: hardware access
- desire for high performance
- issue of implicit trust
- strict backwards compatibility requirements
- Sites can:
	- download content from anywhere
	- spawn worker processes
	- open sockets to a server or even another user's browser
	- display media in a huge number of formats
	- run custom code on the GPU
	- save/read data from the filesystem

### HTTP Protocol
- client/server protocol
- stateless
- requests and headers must have a header
	- body is optional
	- GET and POST are 99.9% of all http requests

### Sending Data over HTTP
- Four ways to send data:
	- embedded in the URL
	- in cookies
	- custom HTTP request header
	- HTTP request body

### Cookies
- basic mechanism for persistent state
- often used for authentication, identification, user tracking

### Same Origin Policy
- subjects from one origin cannot access objects from another origin
	- basis for classic web security
	- some exceptions to this policy
	- relaxed over time to make sharing easier

### Web Server Scripting
- allows easy implementation of functionality
- scripts installed on the web server and return HTML as output that is then sent to the client
- code-reuse reduces the implementation code, but could increase the attack surface

### Unvalidated Input
- client side verification mechanisms are easily bypassed, leaving the web application vulnerable 

### SQL Operations
- Common Operations:
	- CREATE TABLE
	- INSERT
	- UPDATE
	- DELETE
	- SELECT
- Common SELECT modifiers
	- ORDER BY
	- UNION
- Comment: --

### SQL Injection
- insufficient sanitization could lead to modification of query semantics
- Possible Attacks:
	- Confidentiality: modify queries to return unauthorized data
	- Integrity: modify queries to perform unauthorized updates
	- Authentication: modify query to bypass authentication checks

### SQL Injection Defenses
- sanitization
- prepared statements

### Session Management and Authentication
- authentication: strongly connect to session management
- protect session ID

### Session Attack
- interception: intercept a request or response and extract session ID
- Prediction: predict the session ID
- Brute force: make many guesses about the session ID
- Fixation: make the victim use a certain session ID

### Cross Site Scripting (XSS)
- running code from untrusted origin
- allowing user input to be interpreted as document structure can lead to malicious code execution
- Types of XSS:
	- Reflected:
		- code is include as part of a malicious link
		- code included in page rendered by visiting link
	- Stored:
		- attacker submits malicious code to server/database
		- server app persists malicious cdoe to storage
		- victim accesses page that includes stored code
	- DOM-Based:
		- purely client-side injection
- Mitigations:
	- don't trust user input
	- implement output encoding
	- perform user input validation
	- defense in depth / layered defense
	- penetration testing