
2025-08-25     // never thought to make this before

Tags: [[Computer Architecture]] [[Data]] [[Programming]]
# Integer Overflow
> Integer overflow is when we try to represent a number that exceeds the bounds of what our register can hold. If we exceed the size of a register from the positive side by one then our number will wrap around an become the smallest number the register can represent.

It can be difficult to notice if an integer overflow is occurring in a program, if you get a negative when expecting a positive that is an easy indicator. If you're getting a positive it can be difficult though, if you suspect an integer overflow try using a ```long``` or a ```long long``` and check if the output changes, if it does then there is an issue.

**Detection**: Compilers can add extra instructions to check for overflows and throw instructions, though several languages (in my experience this includes C and Golang) won't do that since it adds overhead.

# References
[[two's complement]]