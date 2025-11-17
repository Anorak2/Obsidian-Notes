
2025-11-16

Tags: [[EECS 677 - Software Security Evaluation]] [[Security]]
# Control Flow Integrity
So the problem is rather simple, it's when the program jumps to places where it shouldn't which is often used as an attack vector. The problem is how to implement?
#### Naive Approach
What if we just encode the entire [[Control Flow Graphs (CFG)|ICFG]] into the program text?
#### Practical: Intel CET
Intel's Control-flow Enhancement Technology is a practical solution to this problem, though it requires both recompilation and **hardware support**.

**Scope:**
1. (SHSTK) – Shadow Stack: Prevent ret overwriting with a shadow stack
2. (IBT) – Indirect Branch Tracking: Prevent indirect jumps into gadgets

#### Practical: Control Flow Guard (history)
Control flow guard was created by Microsoft as an attempt to make exploitation financially infeasible or impossible. It didn't have a formal threat model early in development but it was thought of as a way to kill ROP.

Details
- Precision: call needs to be a valid function entry point
- Enforcement: OS verifies indirect control transfer destinations via a table in protected memory
Protections
- Protected destinations page in read-only memory
- Read-only memory bit can be turned off by attacker
# References
[[Buffer Overflows]]

[[Control Flow Graphs (CFG)]]
