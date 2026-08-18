
2025-01-29

Tags: [[Operating Systems]] [[Operating Systems]]
# OS Memory Hierarchy

The Memory hierarchy, with the faster but more expensive options listed first 
1. Registers   (1 cycle)      
2. Cache   (~10 cycles)
3. Main memory(RAM)   (~100 cycles)
4. solid state disk    (~1M cycles)
5. hard disk   (~10M cycles)
6. optical disk
7. magnetic tapes

**Services**
The major categories that an OS needs to be able to handle are:
- File system service; Read/write/create/delete/search, see file information, and permission management
- Communications; Share information between processes in either the same computer or between computers over a network
- Resource allocation; CPU cycles, main memory space, file space, I/O devices
- Accounting; Keep track of who uses what for how much
- Security; Login, admins vs normal users vs guests
- Protection; Prevent memory corruption between multiple user programs and between user programs and the kernel

**System Calls**
These are the interface the OS provides to programs that run on your computer. They are typically written in a high level language like C and most programmers don't use them directly. Types of system calls exist for all of the previously mentioned services, such as open() createfile() chmod() write() etc.

# References

