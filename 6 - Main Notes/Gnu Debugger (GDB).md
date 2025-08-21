
2025-05-13

Tags: [[Reverse Engineering]] [[EECS 678 Final]] [[Programming]] [[Processes]]
# Gnu Debugger (GDB)
```b *0xADDR``` 
	to set a break point at an arbitrary point in memory
	
```layout asm```
	to show a screen with the assembly code
	
```si```
	Steps one instruction

```c```
	continue running the program until it exits or until we hit another breakpoint

```x/x 0xADDR```
	prints the memory value at the location 
**Printing**
- d - default for decimal
- x - Hex
- s - string
- i - instruction
- * - address
We can also use something like 16s to print out 16 strings in a row.
# References

