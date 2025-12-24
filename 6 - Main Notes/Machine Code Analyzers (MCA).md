
2025-12-20

Tags: [[Performance Measurement & Reliability]]
# Machine Code Analyzers
A machine code analyzer is a program that takes a small snippet of assembly code and simulates its execution on a particular micro-architecture using information available to compilers. It also outputs the latency and throughput of the whole block, as well as cycle-perfect utilization of various resources within the CPU.
## EX: llvm-mca
llvm-mca is a performance analyzer tool that uses llvm to measure the performance of machine code for a cpu. When given a sequence of assembly code llvm-mca estimates the Instructions per cycle (IPC), see the cpu architecture notes, and hardware resource pressure.

Ex: Piping straight from Clang on my system
```
clang foo.c -O2 --target=x86_64-linux-gnu -S -o - | llvm-mca -mcpu=btver2
```

Output Snippet on -O0
```
Iterations:        100
Instructions:      7800
Total Cycles:      11839
Total uOps:        8000

Dispatch Width:    2
uOps Per Cycle:    0.68
IPC:               0.66
Block RThroughput: 50.0


Instruction Info:
[1]: #uOps
[2]: Latency
[3]: RThroughput
[4]: MayLoad
[5]: MayStore
[6]: HasSideEffects (U)

[1]    [2]    [3]    [4]    [5]    [6]    Instructions:
 1      1     1.00           *            pushq	%rbp
 1      1     0.50                        movq	%rsp, %rbp
 1      1     0.50                        subq	$16, %rsp
 1      1     1.00           *            movq	%rdi, -8(%rbp)
 1      1     1.00           *            movl	%esi, -12(%rbp)
 1      1     1.00           *            movl	$0, -16(%rbp)
 1      3     1.00    *                   movl	-16(%rbp), %eax
 1      3     1.00    *                   movl	-12(%rbp), %ecx
 1      1     0.50                        subl	$1, %ecx
 1      1     0.50                        cmpl	%ecx, %eax
 1      1     0.50                        jge	.LBB0_4
 1      1     0.50                        callq	rand@PLT
 1      1     0.50                        movl	$32000, %ecx
 1      1     0.50                        cltd
 2      25    25.00                 U     idivl	%ecx
```
Something interesting is that this shows the 64 bit signed division, `idivl %ecx` takes a whopping 25 cycles to perform just that one instruction. However all of this information is actually just available in the instruction tables for each language, so while interesting this isn't the bulk of what llvm-mca does.

```
Resources:
[0]   - JALU0
[1]   - JALU1
[2]   - JDiv
[3]   - JFPA
[4]   - JFPM
[5]   - JFPU0
[6]   - JFPU1
[7]   - JLAGU
[8]   - JMul
[9]   - JSAGU
[10]  - JSTC
[11]  - JVALU0
[12]  - JVALU1
[13]  - JVIMUL


Resource pressure per iteration:
[0]    [1]    [2]    [3]    [4]    [5]    [6]    [7]    [8]    [9]    [10]   [11]   [12]   [13]   
20.99  21.01  50.00   -      -      -      -     27.00  1.00   18.00   -      -      -      -     

Resource pressure by instruction:
[6]    [7]    [8]    [9]    [10]   [11]   [12]   [13]   
 -     27.00  1.00   18.00   -      -      -      -     
                                                                                  
                                                                                  
[6]    [7]    [8]    [9]    [10]   [11]   [12]   [13]   Instructions:
 -      -      -     1.00    -      -      -      -     pushq	%rbp
 -      -      -      -      -      -      -      -     movq	%rsp, %rbp
 -      -      -      -      -      -      -      -     subq	$16, %rsp
 -      -      -     1.00    -      -      -      -     movq	%rdi, -8(%rbp)
 -      -      -     1.00    -      -      -      -     movl	%esi, -12(%rbp)
 -      -      -     1.00    -      -      -      -     movl	$0, -16(%rbp)
 -     1.00    -      -      -      -      -      -     movl	-16(%rbp), %eax
 -     1.00    -      -      -      -      -      -     movl	-12(%rbp), %ecx
 -      -      -      -      -      -      -      -     subl	$1, %ecx
 -      -      -      -      -      -      -      -     cmpl	%ecx, %eax
 -      -      -      -      -      -      -      -     jge	.LBB0_4
 -      -      -      -      -      -      -      -     callq	rand@PLT
 -      -      -      -      -      -      -      -     movl	$32000, %ecx
 -      -      -      -      -      -      -      -     cltd
 -      -      -      -      -      -      -      -     idivl	%ecx
 -     1.00    -      -      -      -      -      -     movq	-8(%rbp), %rax
 -     1.00    -      -      -      -      -      -     movslq	-16(%rbp), %rcx
 -      -      -     1.00    -      -      -      -     movl	%edx, (%rax,%rcx,4)
```

This is the section of the code that is most interesting, as it shows the resource pressure for each individual instruction. These can cause structural hazards in the code and can often become bottlenecks.

### Timeline Analysis
Something else you can do is a **timeline** view using `--timeline`. In this view
- D : dispatched, or sent to the cpu to execute
- = : instruction already dispatched, waiting to be executed. This is actually the effects of data hazards (data not ready yet) and structural hazards (resources busy)
- e : instruction executing
- E : Instruction executed
- R : instruction retired
- - : instruction executed, waiting to be retired

``` Sample view
Timeline view:
                    0123456789          0123456789   
Index     0123456789          0123456789          012

[0,0]     DeER .    .    .    .    .    .    .    . .   pushq	%r15
[0,1]     D=eER.    .    .    .    .    .    .    . .   pushq	%r14
[0,2]     .D=eER    .    .    .    .    .    .    . .   pushq	%rbx
[0,3]     .DeE-R    .    .    .    .    .    .    . .   cmpl	$2, %esi
[0,4]     . DeE-R   .    .    .    .    .    .    . .   jl	.LBB0_3
[0,5]     . DeE-R   .    .    .    .    .    .    . .   movl	%esi, %r15d
[0,6]     .  DeE-R  .    .    .    .    .    .    . .   movq	%rdi, %r14
[0,7]     .  DeE-R  .    .    .    .    .    .    . .   addl	$-1, %r15d
[0,8]     .   D---R .    .    .    .    .    .    . .   xorl	%ebx, %ebx
```
Given this view I can speculate, for example,  that the second and third pushes were delayed due to a structural hazard

### Bottleneck Analysis
While the previous approaches are very useful, another tool in our kit is ``--bottleneck-analysis`` which will report any resource or data dependency bottlenecks discovered.
For example in my test bench I've been using on O0 several bottlenecks were found
```
 +----< 100.  movslq	%eax, %r14
 +----> 101.  imulq	$1801439851, %r14, %rax           ## REGISTER dependency:  %r14
 +----> 102.  movq	%rax, %rcx                        ## REGISTER dependency:  %rax
 +----> 103.  shrq	$63, %rcx                         ## REGISTER dependency:  %rcx
 |      104.  sarq	$53, %rax
 +----> 105.  addl	%ecx, %eax                        ## REGISTER dependency:  %rcx
 +----> 106.  imull	$5000000, %eax, %eax              ## REGISTER dependency:  %eax
 +----> 107.  subl	%eax, %r14d                       ## REGISTER dependency:  %eax
 +----> 108.  movslq	%r14d, %rbx                       ## REGISTER dependency:  %r14d
 |      109.  leaq	(,%rbx,4), %rdi
 |      110.  callq	malloc@PLT
 |      111.  movq	%rax, %r12
 +----> 112.  cmpl	$2, %ebx                          ## REGISTER dependency:  %rbx
 +----> 113.  jl	.LBB3_3                                   ## REGISTER dependency:  %flags
 |      114.  leal	-1(%r14), %r15d
```

# References
- [[LLVM Bitcode]]
- [[CPU Data Path| Data Path (+Information about IPC)]]
- [llvm-mca docs](https://llvm.org/docs/CommandGuide/llvm-mca.html)
- [Algorithmica](https://en.algorithmica.org/hpc/profiling/mca/)
- [[Multi-Data Path and Pipelining]]
