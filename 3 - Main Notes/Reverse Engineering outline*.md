
2025-02-28

Tags: [[Reverse Engineering]] 
# Reverse Engineering outline
Common Static Analysis tools:
- file, head, ldd, xdd, nm, strings, objdump
Common Dynamic Tools:
- strace, ltrace, gdb


## 1. Find the File Type
- Some kind of text file containing printable characters
- Executable
- Data
- Something else like a tar

**some possible tests*
- File-system tests using Stat
- Magic tests - Check for a magic number in a preset position
- Language Tests


# References

