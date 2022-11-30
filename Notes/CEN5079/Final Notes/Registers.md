### Computer Architecture
- Two main parts
	- CPU
	- Memory

### CPU
- control unit
	- retrieve/decode instructions
	- retrieve/store data in memory
- execution unit
- registers
	- internal memory for variables
	- high-speed, special memory locations
- flags
	- used to indicate events when executing instructions
- Program Counter
	- holds memory address of next instruction
- Instruction Decoder
	- makes sense of the instruction
- Data bus
	- connects memory and CPU

### Registers on x86
- General Purpose Registers
	- %eax, %ebx, %ecx, %edx, %edi, %esi
- Special Purpose Registers
	- %ebp, %esp, %eip, %eflags
- Indirect/register address mode
	- take address thats stored in a register
- indexed address mode
	- take address in register and add an offset

### Anatomy of the Code
- .section breaks up the program into sections
- .data is used for variables and data you might need
- .text is the code of the program you write
- .globl `_start` indicates that `_start` is a symbol, required by the linker
	- indicates that the loader will load and start the program from this location