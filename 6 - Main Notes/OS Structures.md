
2025-02-03

Tags: [[kernel]] [[Operating Systems]] [[Operating Systems]]
# OS Structures
### MS DOS
- Written to provide the most functionality in the least space
- Minimal functionality
- Divided into modules
![[Pasted image 20250203141515.png]]

### UNIX: Monolithic Kernel
![[Pasted image 20250203141717.png]]
- Implements the CPU scheduling, memory management, file systems, and other OS modules into a large block

Pros:
- low overhead
- Data sharing is easy
Cons:
- Too big (device drivers)
- One bug can crash the whole program

### Loadable Kernel Module
- This is similar to the last model except we dynamically load and unload code when we need it
- This is what Linux and most of today's OS's use
Pros:
- Don't need to have every driver in the kernel
- Easy to expand the kernel
Cons:
- A bug in a module can crash the whole program (Crowdstrike)
### Micro-kernel
![[Pasted image 20250203142004.png]]
- Moves as much as it can from the kernel into the user space
- Communicate among kernels using message passing
Pros:
- Easy to use
- More reliable since less code running in kernel mode
Cons:
- Performance overhead of user space to kernel space communication

### Hybrid
Most Modern Operating systems aren't purely one model, and they can mix and match. For example Linux and Solaris use monolithic, plus modular for dynamic loading of functionality. Windows is mostly monolithic with different subsystem personalities.

# References

