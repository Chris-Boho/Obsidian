### Buffer Overflow
- program attempts to store data beyod the boundaries of the a buffer, overwriting adjacent memory locations
- results from:
	- mistakes 
	- unfamiliarity with language
	- ignorance about security issues
	- unwillingness to take any extra effort
- common targets:
	- setuid/setgid programs
	- network servers
- goals:
	- force program to execute operations
	- inject code into memory process
	- change flow of control to execute that code

### Stack
- every function gets a frame on the stack
	- create when function is called
	- contains local, in scope variables
	- frame destroyed when function exits
- frames contain control flow information
- ESP register points to the top of the stack
- EBP register points to the current frame

### Return address
- tells the function where to resume executing after the function is complete
- invisible to programmer
- when function is invoked, calling point is saved
- when function completes, returns to initial calling point

### Example
 ![[Stack Frame Example.png]]

### Dangerous Functions
- strcpy
- strcat
- gets
- scanf

### Return Oriented Programming (ROP)
- reuses gadgets
	- small sequences of instructions ending in a return
- each gadget performs small update to program
- execution becomes a chain of returns to gadgets
- works against every architecture
- useful in:
	- non-executable memory regions
	- signed code

### Return to Libc
- subvert vulnerable program's execution flow by re-using existing executable code from the standard C library shared object

### Mitigations
- write secure code
- test programs with focus on security issues
- switch to more secure libraries33
- 'canary'
	- terminator canary
		- contain string terminator (`\0`) to stop string copy routines
	- random canary
		- contain random value generated at program initialization and stored
	- random XOR canary
		- random value XOR'd with the control data 
- Non-executable stack
- address space randomization
	- randomly arranging the positions of key data areas