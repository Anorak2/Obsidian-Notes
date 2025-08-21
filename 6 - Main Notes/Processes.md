
2025-02-03

Tags: [[Operating Systems]] [[Operating Systems]]
# Process
A process is an OS abstraction that represents a running application, and a process has three main components.
1. Address Space, this is the process's view of memory. This includes program code, global variables, stack, etc.
2. CPU context (Process state); This is the program counter (PC), stack pointer, and other CPU registers
3. OS Resources; This is various OS resources that the process uses, things like open files, sockets, etc.

### Program address space
- Text, this is the program code
- Data, Global variables
- Heap, dynamically allocated memory (such as malloc)
- Stack, temporary data that grows at each function call

### Process Control Block (PCB)
This stores the information associated with each process
- Process Id
- Process State
- Saved CPU registers
- CPU scheduling information
- Memory-management information
- Accounting information
- OS resources
### Process Scheduling
Decides which process to run next among ready processes

OS maintains multiple scheduling queues:
- Ready Queue
- Device Queue

### Context Switching
- Save the current state, and load up the data for a new state. We also have the change the address state and other info in the [[Process Control Block|PCB]] 
- by doing this we are pausing one program, and later on we can continue running it.
- Doing this adds a significant amount of overhead if we do it to much
- On a Xeon 2.8Ghz context switching can have a cost of about 1.8 us, or ~5040 cpu cycles

### Process Creation
- Processes stem from a parent process, so we will always end up with a process tree
# References

