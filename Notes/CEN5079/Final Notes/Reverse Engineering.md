- process of analyzing a system
- understanding its structure and functionality
- used in different domains
- understand architecture
- extract source code
- change code functionality
- understand message exchange

### Going Back is Hard
- disassembling problems
	- hard to distinguish code from data
- de-compilation problems
	- structure is lost
		- data types are lost
		- names and labels are lost
	- no one-to-one mapping
		- same code can be compiled into different assembler blocks
		- assembler block can be the result of different pieces of code

### Byte Code
- byte code is 'interpreted' and run in a virtual machine
	- JVM
- easy to decompile
	- JAD
- obfuscation is used to increase security
	- still not impossible to read

### Static Analysis 
- identify the file type and its characteristics
- extract strings
- identify libraries and imported symbols
- disassemble
	- program overview
	- finding and understanding important functions

### Dynamic Analysis
- memory dump
	- extract code after decryption 
- library/system call/instruction trace
	- determine the flow of execution
	- interaction with OS
- Debugging running process
	- inspect variables
	- data received by network
	- complex algorithms
- Network Sniffer
	- find network activities
	- understand the protocol
- running the malware and observing its behavior on the system
- requires setting an environment
- malware should be run in a controlled environment called sanbox
- Advantages:
	- can inspect actual program behavior and data values
	- target of indirect jumps can be observed
- Disadvantages:
	- may accidentally launch attack/malware
	- anti-debugging mechanisms
	- not all possible traces can be seen
- System calls
	- at boundary between user space and kernel
	- reveal much about a process' operation
	- strace