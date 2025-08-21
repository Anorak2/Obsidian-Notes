
2025-04-21

Tags: [[Security]] [[Reverse Engineering]]
# Binary Rewriting
Binary rewriting is where we change a compiled binary program by altering, inserting, or deleting instructions so that we can manipulate its behavior. Doing this even has numerous non-malicious applications like doing virtualization, hardening, debugging, or optimization.

**pre-load libraries**
This is an easier hack to do, and it works by using ```LD_PRELOAD``` since the way the libraries are found since the first definition the dynamic linker finds is used. By using that function we can load our user generated code before any of the libraries code is initialized, meaning we can overwrite any library function that we want to and inject our own functionality. This technique is only allowed for binaries already owned by the user, meaning that as an actual attack it isn't the most useful.

```LD_PRELOAD=./lib.so ``` when running

**how debuggers work** 
for debuggers like gdb that work without slowing down the program we need operating system support so that we can interact with our program. gdb does that by spawning in our program as a child program and then using the ```PTRACE``` API so that the parent can interact with the child process. ```PTRACE``` includes functions to read/write the child's registers, do single step process execution, or to just kill/send interrupts.
![[Pasted image 20250513233620.png]]

# References

