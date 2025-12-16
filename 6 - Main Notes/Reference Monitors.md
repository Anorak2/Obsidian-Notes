
2025-11-16

Tags: [[Software Security Evaluation]] [[Dynamic Analysis]] [[Security]]
# Reference Monitors
Often detection might not be enough, so what if instead we try to keep "bad" things from happening during execution. In the simple version we just kill the program if something bad is happening, though we may also try to sanitize the data.

**The Big Idea:** To make sure programs are behaving well we:
- articulate a policy for allowed behavior
- Keep a running record of security relevant behavior
- Prevent a violation of the policy 

## Ref Monitor Design
There are many considerations we have to make when designing a reference monitor and several different designs. We have to decide how close it is to the program, whether inline or or external. We also have to choose a design, some common ones listed below:
- Kernelized: baked into the kernel, this makes it coarse, and secure/hard to avoid
- Wrapper: creates a special execution environment
- Inline: rewrite the program/hook syscalls: this approach is precise, but less secure/easier to avoid

**Important Properties:**
- Memory Safety. Programs respect aggregate type sizes, process boundaries, code v data
- Type Safety. e.g. Functions and intrinsic operations have arguments that adhere to the type system
- Control Flow Safety. e.g. . All control transfers are envisioned by the original program

## Various
---
**OS as a reference monitor**
The OS keeps a collection of running processes and files where processes are associated with users and files have ACL's (access control lists). The OS automatically enforces various policies like file access and process space writes.

**Software Fault Isolation**
Isolate processes such that even on shared hardware each process is a logical fault domain. This also means we have to ensure that all memory references and jumps are within the process fault domain.

**Inline Reference Monitors: SASI**
SASI is a Cornell project for inline policy enforcement where we can change the program to enforce “any” safety policy. We do this by expressing allowed behavior as a FSM. Some common examples are no division by zeroes and no network send after a file read.

One benefit to SASI is that it attempts to reduce the performance cost, for example we only need to check for a divide by zero before a DIV instruction.
# References
[[Side Channel Attacks]]

[[Finite State Machines]]