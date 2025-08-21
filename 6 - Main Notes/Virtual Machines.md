
2025-04-28

Tags: [[Operating Systems]] [[Operating Systems]]
# Virtual Machines
This the the technology that allows for cloud computing, and the basic idea is that virtual machines allow for us to provide abstractions of machines. The benefits are that we can run multiple operating systems each with its own VM. We can also copy a VM image and run it on a different machine, and also create a snapshot of the state and restore it later. We can also have a more efficient resource utilization.

Downsides?
- Overhead
- Interference

**Native vs Hosted**
Native, or type 1, is a virtual machine manager that runs directly on top of the bare hardware. There are also hosted VMMs which which run within an OS, but obviously this adds another layer and more overhead and thus less ideal if you only care about the machines.

**Virtualizing Hardware**
For virtualizing the cpu one or more ```vCPU's``` are created for every VM though on the host they are seen as real. We do this by time slicing the CPU and scheduling like any other OS.
# References

