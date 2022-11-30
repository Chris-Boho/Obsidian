### Mitigations
- authentication
- access code
- firewall
- anti-virus
- logging

### Process Isolation 
- processes can't read/write memory arbitrarily
- processe can't access devices directly 
- Hardware support:
	- protected mode execution
	- virtual memory

### Protected Mode
- Ring 0: OS
	- code may directly access any device
	- may change protection level of the CPU
- Ring 1, 2: Device Drivers
	- may directly access some devices
	- may not change the protection level of the CPU
- Ring 3: Userland
	- may not directly access devices
	- all devices must be via OS APIs 
	- may not change the protection level of the CPU
- if a ring 3 process tries to access CR0/3 register, halt, sti/cli, int/out, it immedietly crashes

### Virtual Memory
- creates the illusions that each process runs in its own, empty memory space
- proccesses cant read/write memory used by other processes / OS
- each process has a page table that maps virtual space into physical space
- CPU translates virtual addresss to physical address on-the-fly
- OS creates the page table for each process
- if a process tries to read/write memory outside of its page table
	- seg fault
	- page fault
	- process crash