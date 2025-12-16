
2025-09-29

Tags: [[Software Security Evaluation]] [[Security]] 
# Buffer Overflows
A buffer overflow is a type of security exploit where a malicious actor is able to write to memory outside of the allocated buffer. Historically this was often done by bringing your own script by injecting it into the buffer with a NOP sled which would hijack the program's control flow.  There are a number of countermeasures, as listed below, that makes it significantly harder to hijack control flow but the fundamental problem is still present.

## Countermeasures

**Stack Canaries:** 
> Stack canaries, named for their analogy to a canary in a coal mine, are used to detect a stack buffer overflow before execution of malicious code can occur. This method works by placing a small integer, the value of which is randomly chosen at program start, in memory just before the stack return pointer. Most buffer overflows overwrite memory from lower to higher memory addresses, so in order to overwrite the return pointer (and thus take control of the process) the canary value must also be overwritten. This value is checked to make sure it has not changed before a routine uses the return pointer on the stack. This technique can greatly increase the difficulty of exploiting a stack buffer overflow because it forces the attacker to gain control of the instruction pointer by some non-traditional means such as corrupting other important variables on the stack.

**W xor X:**
$W \bigotimes X$ is a hardware extension that ensures every byte is *either* executable or writable but never both. If your program ever tried to write to an executable byte then it would simply crash.

**ASLR:** 
Also known as Address Space Layout Randomization, this technique randomizes the addresses of all sensitive parts of the program including the base of the executable, stack, heap, and libraries. This technique can make it more difficult for an attacker to reliably interact with the program since its harder to predict target addresses.

**Control Flow Integrity (CFI):** 
CFI is a security technique that was introduced prior to W ^ X becoming more common and it aims to limit the ability of indirect transfers such as jumping to a location stored in memory/cpu register rather than written in the code.

## ROP
ROP, or return oriented programming, is a technique that is able to bypass every previous method that was mentioned. ROP works by hijacking the call stack and then carefully running sections of code (gadgets) already present in memory. This is incredibly difficult to do anything about because these gadgets when chained together can perform arbitrary operations. For example it's been proven that using components of libc an attacker's options are Turing complete.

# References
[[Threat Models]]
