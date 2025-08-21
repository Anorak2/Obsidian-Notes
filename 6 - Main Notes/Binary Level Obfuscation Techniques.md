
2025-05-13

Tags: [[Reverse Engineering]]
# Binary Level Obfuscation Techniques
Obfuscation at the binary level manipulates machine code to confuse disassemblers, debuggers, and reverse engineers.

**Cyclomatic Complexity**
Cyclomatic Comp = (# of edges in CFG) - (# of nodes in CFG) + 2(# of conditional nodes in CFG, also known as number of connected components)

We can just calculate this using a default Ghidra script though ```calculateCyclomaticComplexity```.

**Obfuscator LLVM**

#### Substitution
Full list: [link](https://github.com/obfuscator-llvm/obfuscator/wiki/Instructions-Substitution)
Substitution passes are a type of code obfuscation technique where parts* of a program are replaced (substituted) with functionally equivalent but syntactically different versions.
![[Pasted image 20250513225400.png]]
^ example of how it works in O-LLVM

In Ghidra, any "not" is represented as ```a ^ 0xffffffff```
#### Bogus Control Flow
branches and control paths are inserted into a program’s code. These paths look valid but are never executed (or do nothing meaningful). These are somewhat easier to spot/sift through in Ghidra’s control flow graph.

In O-LLVM, “This method modifies a function call graph by adding a basic block before the current basic block. This new basic block contains an opaque predicate and then makes a conditional jump to the original basic block. The original basic block is also cloned and filled up with junk instructions chosen at random.”
![[Pasted image 20250513225705.png]]

#### Control Flow Flattening
![[Pasted image 20250513225840.png]]
Control flow flattening is an obfuscation technique where the natural, structured flow of a program (like if/else, loops, and returns) is rewritten into a flat structure using a dispatcher or state machine. This makes the control flow non-linear.

The method O-LLVM uses extends a method written by T. L´aszl´o and A. Kiss, but the most important thing to know is that unlike the original, O-LLVM fully flattens the flow.
# References

