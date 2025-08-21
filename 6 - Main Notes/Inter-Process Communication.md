
2025-02-07

Tags: [[Operating Systems]] [[Operating Systems]]
# Inter-Process Communication

Though we want processes to be separate, there are valid reasons to have communication between processes. For example, each Chrome thread is a separate process so that we can have data isolation.

**Shared Memory**
- Share a region of memory between co-operating processes
- read or write to the shared memory region
- ++ This method is fast, there is a one time cost but after that there just is no cost
- -- Downside is that we have to coordinate, two processes can't write over the same space at the same time. This synchronization is actually very difficult

**Message Passing**
- Exchange messages (send and receive)
- typically involves data copies (to/from buffer)
- ++ No data corruption or having to deal with synchronization
* -- More overhead 

**Pipe**
These are the most basic form of IPC and it uses unidirectional communication when the processes are on the same OS. Pipes only exist until the processes exist and data can only be collected in a FIFO order.

**FIFO** (Named Pipe)
These are more powerful than anonymous pipes since there is no parent/sibling relationship needed, they allow for bidirectional communication, and FIFO's exist even after the creating process is terminated

FIFO's appear as typical files, and communicating process must reside on the same machine.

**Sockets**
These are a two way communication pipe and they are the backbone of internet services. We can have a bunch of different types such as UNIX domain sockets, client/server sockets, and socket communication modes such as TCP and UDP.
# References
[[Processes]]
