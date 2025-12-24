
2025-08-22

Tags: [[Software Security Evaluation]] [[Code Abstraction Formats]]
# LLVM Bitcode
> LLVM stands for low level virtual machine and it is a set of program manipulation tools built around a "mid-level" abstraction instruction set, and it is really a language independent framework.

It's called a intermediate representation (IR) because it sits between the source code and executable, and importantly it is high level enough to avoid an architecture lock in while being low level enough to optimize / provide explicit details.

**Bit code:** Bitcode is an IR that is universal and human readable, it's relatively generic and relatively easy to analyze. LLVM Bitcode has a nested structure with modules that have functions and globals that then have locals, instructions, and registers. Notably no real computer can natively run bitcode, it is a high level representation and it needs to be converted first.

**Bitcode Memory:** There are no explicit layout between objects, an infinite amount of registers also which is important since SSA is enforced

## Examples
C```
```
int main(int argc){
	return argc + 5
}
```
Equivalent Bitcode:
```
define i32 @main(i32 %argc) {
	%val = add i32 %argc, 5
	ret i32 %val
}
```
Generally it is not ok to nest multiple instructions in LLVM, there is no return and add function. Also the % is how we invoke a register, and registers can have any name.

## Pointers
```%reg == alloca i32, align 4```
Here %reg has the type i32*, so a pointer to an i32. There is also a generic pointer type that leaves out the type


# References


