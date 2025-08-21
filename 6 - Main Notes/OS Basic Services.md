
2025-01-31

Tags: [[Operating Systems]] [[Operating Systems]] [[kernel]]
# OS Basic Services
File system service:
- Read/write/delete/search files and directories
- See file information
- Permission Management

Communication:
- Sharing info between processes in the same computer

Resource Allocation
- CPU cycles, main memory space, file space, I/O devices

Accounting:
- Who uses how much and for what

Security:
- Login, administration of users

Protection:
- Prevent memory corruption between multiple user programs and between user programs and the kernel
- Detect and report errors

**System Calls:**
- System calls are the programming interface to the services provided by the OS, and this is how we can use the OS as a programmer.
- Typically written in a higher level language (C)
- Most programmers don't directly use system calls
	- higher level APIs like libraries
	- System programmers do use system calls
- Most popular system call APIs
	- POSIX for POSIX based systems (Unix, Linux, and Mac os)
	- Win32 API for Windows
- It can be hard to tell which calls are system calls, but we can just ask the system or check man pages

Types of system calls
- Process control, create/terminate a process, get/set process attributes

**MIcro-kernel**
This is the layer that moves as much from the kernel into user space
communicate among kernels and user via message passing

# References