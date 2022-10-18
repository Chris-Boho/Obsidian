## Threat Modeling

- Process of Systematically Identifying Threats faced by the System

1. Identify things of value that you want to protect
2. Enumerate the Attack Surfaces
3. Hypothesize attackers and map them
	- Things of Value they want (1)
	- Their ability to target vulnerable surfaces from (2)
4. Survey Mitigations
5. Balance cost versus risks 

You start your internship in a vending machine manufacturing company. Your first task is to perform threat modeling to build more secure vending machines. Please explain the threat modeling steps **wrt this scenario (i.e., Vending Machine).** 

Your Answer:

1.  The first thing to consider are the items of value inside a vending machine, which are the snacks/drinks and the money.
2.  The second thing to consider would be how the vending machine could be attacked. For example, the window could be broken into to take the snacks. The lock can also be picked to steal the money.
3.  Next is to guess who might try to target the vending machine. A possible attacker like a thief would use a tool like a crowbar to smash the window. It would also be possible to just steal the vending machine in it entirety.
4.  Next is to figure out how to mitigate these attacks. A metal cage could be added around the vending machine, so they can't break into it normally. If it is bolted or nailed down then it would also prevent an attacker from loading it on his truck.
5.  The final step would be to figure out if this would be worth the cost in money to implement these mitigations. If a vending machine outside a police station rarely ever gets attacked, then there's no reason to add an expensive metal cage to it.

- Review our example cast of attackers, they may come in handy if you are asked to develop a threat model on the exam.

## Security Architecture

#### Design Principles 

- #### Economy of Mechanism
	- design should be as simple as possible
	- black-box / functional testing
- #### Fail-safe defaults
	- deny as default action
		- grant access only on explicit permission
	- new accounts dont have admin privileges
	- minimum password length
	- files are write protected
- #### Complete Mediation
	- complete access control
		- check every access to every object
		- identification of authentication for action
	- trusted path
		- make sure user is talking to authentication program
		- any value that can be influenced by user cannot be trusted
- #### Open Design
	- open source
	- a system should be secure even if the adversary knows everything about its design
	- doesnt not include things like secret keys
	- allows review
	- established trust
	- security depends on secrecy of few, small tokens
		- keys 
		- passwords
- #### Separation of Privilege
	- Access depends on more than one condition
		- for example, two keys are required to access a resource two privileges can be physically distributed
		- EX: launch of nukes requires two people
	- Compartmentalization (isolation)
		- break system in different parts
		- minimize privileges in each part
		- dont implement all or nothing model
			- minimizes possible damage
	- Sandbox
		- java sandbox 
		- VM's 
	- Authorization should only be provided to those who require it
		- not everybody needs to be able to do everything
- #### Least Privilege
	- subjects posses the minium required authority to complete their task
- #### Least Common Mechanism
	- Privilege hierarchy 
		- OS
		- Users and Processes with System Privileges 
		- Users and Processes
		- Unprivileged Processes
	- Ring 0 - 3 etc....
- #### Psychological Acceptability
	- easy to use GUI


## Authentication 

- Three Kinds of Secrets:
	1. Something you know
		- a password
	2. Something you are
		- fingerprint 
		- voice scan
		- iris scan
		- face scan
	3. Someting you have
		- smart card
		- smart phone

#### Two Factor Authentication

- Fingerprints:
	- pick up fingerprints using  tape or glue
	- photograph and enhance fingerprint
- Facial Recognition
	- vulnerable to 2d images
	- lifelike masks of target can be crafted
- Voice Recognition
	- attacker can record and play your voice
	- train an AI to mimic your voice
- SMS Two Factor
	- vulnerable to social engineering
	- call company and ask to change phone number
- One Time Passwords / Authenticators
	- generate passcodes that change over time

- Work Factor: how long it takes to accomplish something
	- how long would it take to securely authenticate a user

### Setting permissions
- `chmod [who] < +/- > <permissions> <file1> <file2>`
- who: 
	- omitted -> user, group, and other
	- a -> user, group, and other
	- u -> user
	- g -> group
	- o -> other
- permission:
	- r -> read
	- w -> write
	- x -> execute
- Examples:
	- amin@DESKTOP:~$ `chmod ugo-rwx cs2550`
	- amin@DESKTOP:~$ `chmod go-rwx submission.py`
	- amin@DESKTOP:~$ `chmod u-rw submission.py`
	- amin@DESKTOP:~$ `chmod +x grade`

- `chmod ### <file1> <file2>`
	- `###` corresponds to owner, group, and other
	- each value encodes read, write, and execute permissions
		- 1 -> execute
		- 2 -> write
		- 4 -> read
		- 7 -> set as all
- Examples: 
	- amin@DESKTOP:~$ `chmod 000 cn5079`
	- amin@DESKTOP:~$ `chmod 100 submission.py`
	- amin@DESKTOP:~$ `chmod 777 grade`

## Passwords

- hashed: one-way cryptographic hash functions
	- transforms input data into scrambled output data
- Dictionary Attacks:  method of cracking passwords by trying most common passwords and variations of it; going through a word list

- Honey Words: 
	- store multiple salted/hashed passwords for each user
	- only one of them is the correct password
	- create honeyserver that stores the index of the correct password

- passwords in Linux are stored in /etc/shadow and are typically encrypted in md5crypt

## Web Security 

- Same Origin Policy (SOP):
	- subjects from one origin cannot access objects from another origin
	- basis of classic web security
	- in case of cookies:
		- domains are the origins
		- cookies are the subjects
	- JS from origin D cannot access objects from origin D'
	- JS included in D can access all objects in D
	- Two URL's have the same origin if the protocol, port, and host are the same for both 
	- ![[Same Origin Policy Example.png]]

- HTTP:
	- client/server protocol
	- text-based protocol
	- stateless
	- requests and responses must have a header
	- Request Methods:
		- GET - commonly used
		- POST - commonly used
		- HEAD
		- PUT
		- DELETE
		- TRACE
		- OPTIONS
		- CONNECT
	- Response Status Codes:
		- 1XX - informational
		- 2XX - success
			- 200 OK
		- 3XX - redirection
			- 301 Moved Permanently 
			- 303 Moved Temporarily
			- 304 Not Modified
		- 4XX - client error
			- 404 Not Found
		- 5XX - server error
			- 505 HTTP Version Not Supported

- Cookies:
	- basic mechanism for persistent state
	- used for identification, authentication, user tracking
	- Expiration sets how long cookie is valid

- SQL Injection:
	- queries often involve untrusted data
	- app is responsible for interpolating user data into queries
	- insufficient sanitization could lead to modifciation of query semantics
	- Example: 
	- `amin' or 1=1); --`
	- `$result = mysql_query(“select & from Users where`
	- `(name = ‘amin’ OR 1=1); - -`
	- Defense:
		- Sanitization
		- Prepared Statements

- Session Management:
	- HTTP is stateless
	- web apps must create and manage sessions themselves
	- session data is:
		- stored on the server
		- associated with unique session ID
	- client is informed of session ID and attatches to each request
	- Session IDs must be unique and resistant to brute force attacks
		- hash Session ID
	- Session Fixation:
		- attacker 'fixes' the user's session ID before the user logs into the target server
		- Defense:
			- regenerate session IDs at authentication

- Cross Site Scripting (XSS):
	- steal information from your browser
	- attacker tries to send user to a site controlled by an attacker
	- XSS refers to running code from an untrusted origin
	- Subverting SOP:
		- trick user's browser into thinking that a scripts origin is a certain website's
	- Types of XSS:
		- Reflected:
			- code is included as part of malicious link
			- code included in page rendered by visiting link
		- Stored:
			- attacker submites malicious code to server
			- server app persists malicious code to storage
			- victim accesses page that includes stored code
		- DOM-Based:
			- purely client-side injection