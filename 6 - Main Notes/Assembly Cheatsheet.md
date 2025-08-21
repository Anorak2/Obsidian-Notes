
2025-02-04

Tags: [[Programming]] [[Assembly]]
# Assembly Cheatsheet 
```mov src, dst``` : dst = src
```push src``` : add to top of stack
```pop dst```  : remove from top of stack

```jmp label``` : jump unconditionally to that label
```call addr```  push return address on stack, and then call function at that address
```ret```     Pop return address from stack and return to that address
```syscall``` enter the kernel to perform a system call
```%include "file.asm"```

```and dst, src;  dst &= src```
```or dst, src;   dst != src```
```xor dst, src;  dst ^= src```
```not dst;       dst = ~dst```
```test src1, src2; a bitwise and```


**Registers**

| Register                | Purpose             |
| ----------------------- | ------------------- |
| %rip                    | instruction pointer |
| %rsp                    | stack pointer       |
| %rax                    | Return value        |
| %rdi                    | 1st argument        |
| %rsi                    | 2nd argument        |
| %rdx                    | 3rd argument        |
| %rcx                    | 4th argument        |
| %r8                     | 5th argument        |
| %r9                     | 6th argument        |
| %r10, %r11              | Callee-Owned        |
| %rbx, %rbp, %rb12-%rb15 | Caller Owned        |


# References

