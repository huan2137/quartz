Port-Mapped vs. Memory Mapped IO

Port-mapped I/O is a method of accessing the registers and memory of CPU peripherals using special instructions and I/O ports. These special instructions are defined by the specific instruction set architecture (ISA), and I/O ports are unsigned integers that identify the peripheral's registers and memory words. Programmers have to use I/O ports to specify which registers or memory word is being accessed when doing an I/O operation with a special I/O instruction.

One example of port-mapped is found in the IA-32 ISA family, a set of 32-bit ISAs developed by Intel which formed the foundation of x86 family of processors (most notably the Intel 8086 processor and its successors.) 