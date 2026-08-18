
2026-07-23

Tags: [[Computer Architecture]] [[High Performance Computing - Computer Enhance]]
# 8086 Instruction Decoding
On the 8086 CPU registers were 16 bits and each register of course has a name (ax, bx, cx). When doing something memory was loaded into the register, some operation was performed, and then the data was put back into memory. This is the basis of modern CPU architecture, but instruction decoding is essential since otherwise the computer doesn't know what it needs to do.

**`Mov` Example**
Each instruction corresponds to a name we use to remember it. For example, `mov` copies either data from the disk into a CPU's register or copies data from one register to another. When assembled a command, for example `mov ax, bx`, is encoded into two bytes. One byte is for the instruction, it encodes that this is a `mov` in the top six bits but also two parameters D and W. The second byte encodes the `mod`, `reg`, and `r/m` fields. the `mod` field encodes whether it is a register to register move, a register to memory move, and so on. The `reg` field encodes the register, and the `r/m` encodes either a register or memory. the `d` bit encodes if either `reg` or `r/m` is the destination, the `w` bit encodes if it is sixteen bits or eight bits.

Furthermore, since registers are sixteen bits in order to make use of just 8 bits it can be selected using `al` to represent the low bits, `ah` to represent the high bits, and of course `ax` still represents the whole 16 bits.

Something worth noting is that the `mov` instruction can be between 2-6 bytes long, and that the length can require multiple reads. After the first byte the CPU has to read the second byte just to tell if there are bytes after that one. The register to register `mov` is the simplest while copying between two different `mem8` registers requires 4-6 bytes. This complexity and nesting can seriously slow down the CPU. Moving can also add an effective address computation, where it takes the value in a register plus a constant value in order to find the address.


**8086 Instruction Patterns**
```asm6502
mov ax, [bp]
mov bx, [bp + 2]
add ax, bx
```
This pattern is fine, but if this is the only time bx is used then it is inefficient. 8086 assembly allows for the following pattern for cases like this

```asm6502
mov ax, [bp]
add ax, [bp + 2]
```

This is allowed since the only difference between a move and an add is the opcode, and these patterns exist in many other places. 


# References