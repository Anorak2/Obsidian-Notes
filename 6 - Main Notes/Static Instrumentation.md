
2025-11-16

Tags: [[Software Security Evaluation]]
# Static Instrumentation
Static instrumentation tends to be **easier**, often we do this earlier in development in a basic form by using print statements to see if they get hit and executed. Often Static Instrumentation tools are built directly into compilers, including cases like LLVM coverage tools and GCC coverage tools, there is also google's Closure compiler is also relevant here. 

The **drawback** is that it can be very difficult to predict the path of a program, and with a big enough program it can be excessive to add say a print statement for every if statement.

## Test Coverage
--- 
How do we know if our test suite is sufficient? This is relevant since in our testing we want to make sure we are hitting every (or more likely most) branches/paths so that something isn't being missed. We generally accomplish this by checking how many lines, branches, or paths of the program are covered by the test suite.

**Assessing Coverage**
- Simple: Add a counter for every instruction 
- Better: add a counter for every basic block of code
What information does this approach give us:
- Instruction: Yes
- Branch: Yest
- Path: No

#### Path Profiling
https://dl.acm.org/doi/10.5555/243846.243857
- Intuition: Assign integer values to edges such that no two paths compute the same path sum
- Select edges to instrument using a spanning tree

**Naive Approach**
![[Pasted image 20251116203430.png]]
- Instrument probes at each edge
- Idea is that we don't need an A-> B counter since it's the sum of the B -> C and B -> D counters.
## Using LLVM Instrumentation
this section works using clang++
- `sudo apt install clang++ llvm-dev`

Goal: Asses the coverage of a test suite
Approach: use LLVM's built-in instruction implementation
1. Insert PGO (Profile-guided optimization) probes
2. interpret probes as coverage measurements

Flags:
- `-fcoverage-mapping`
- `-fprofile-instr-generate`: generate profile information at the source instruction level 
- `-fprofile-generate`: generate profile information at the IR level

![[Pasted image 20251116204523.png]]
This will cause the program to emit an additional coverage file in the location of the env variable LLVM_PROFILE_FILE. In our case use 
	`export LLVM_PROFILE_FILE=test1.prof`
This will generate a file that isn't human readable so we'll use extra tools to generate a readable report
![[Pasted image 20251116204832.png]]

![[Pasted image 20251116204848.png]]
# References
[[Dynamic Instrumentation]]
