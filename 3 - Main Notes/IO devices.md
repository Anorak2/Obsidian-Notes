
2025-04-21

Tags: [[Operating Systems]] [[Operating Systems]] 
# IO Subsystems
The goal of IO subsystems is to make it easy to use many different types of devices by providing a standard interface so that the programmer can abstract some of the details. One of the ways we do this is by characterizing devices into buckets that tell us how to treat them, with some examples as follows.

 - Block devices
	– E.g., disk, cd, USB stick
	– High speed, block (sector) level accesses
- Character devices
	– E.g., keyboard, mouse, joystick
	– Low speed, character level accesses
- Network devices
	– E.g., ethernet, wifi, bluetooth
	– Socket interface

Some types of actions we do on these can include
- Blocking I/O  
	- Wait (i.e., the calling process is put to sleep) until the data is ready
- Non-blocking I/O  
	- Immediately return to the caller no matter what.  
	- I/O may not be completed  

- Asynchronous I/O  
	- Notify later when the I/O is completed (via callback or interrupts)

**Communication**
How does the CPU talk to the devices? It doesn't, it talks to the device controllers either using I/O instructions or with memory mapped I/O.

Memory Mapped I/O is when parts of the physical memory space are mapped to the hardware controllers, specifically the control registers and buffers. It's then the device driver's job to handle reading/writing to the device in whatever way.

**Data Transfer Methods**
Programmed I/O (PIO)  
- Via CPU’s load/store instructions  
- Simple h/w, but high CPU load  
- often uses polling

Direct Memory Access (DMA)  
- Controllers directly read/write from/to DRAM  
- Interrupts the CPU on the completion of I/O ops.  
- Complex h/w, but low CPU overhead

# References

