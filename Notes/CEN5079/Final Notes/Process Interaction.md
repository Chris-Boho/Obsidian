### Cat Function
- a process is created
- process is loaded
- process is initialized 
- process is launched
- process reads its arguments and environment variables
- process executes the commands
- process terminates

### Process in Linux
- every process in linux has:
	- state
	- priority 
	- parent, siblings, children
	- shared resources
	- virtual memory space
	- security context
		- effective uid / gid
		- saved uid / gid
		- capabilites
- kernel looks at shebang to find what to load