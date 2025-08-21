
2025-03-24

Tags: [[Operating Systems]] [[Operating Systems]]
# Threads
We want things to run concurrently but without the overhead that processes have, we also don't care about security so we want to share memory easily and to do these things efficiently.

In comes threads, they are a lightweight process. Whereas processes have address space, cpu context, and OS resources threads exist within a process and only need CPU context. Threads have their own independent control flow, stack and thread specific data, and everything else such as the address space, open files, and global vars is shared.

**Benefits**
- Responsiveness since it is a simple model for concurrent activities and we don't need to block I/O
- Resource sharing since we have easier and faster memory sharing
- Economy, threads reduce context switching and space overhead
- Scalability since we can exploit the multicore CPU's

**Kernel level vs User level**
With user level threads the kernel is unaware that there are any threads and the advantage is that there is no kernel support and that they are fast, but the downside is that they block the system call. Kernel level threads are nice because they have no threading runtime and native system call handing, but they have overhead.

There are also technically hybrid threads where we have many kernel threads to many user threads, with the idea that we can get the best of both worlds?
# References
[[Processes]]

[[Parallel Architectures]]