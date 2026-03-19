
2025-05-13

Tags: [[Reverse Engineering]]
# Tracing
**Strace** 
	strace allows to programmer to very quickly find how how a given program is interacting with the OS. When we run strace it will monitor the code using system calls and signals, making it fast.

**ltrace**
	ltrace is strace's cousin and it tracks how a given C program interacts with libraries. 

Addresses:
	to find the addresses run the code with ```-i``` and this is useful because now we can open this in gdb
# References
