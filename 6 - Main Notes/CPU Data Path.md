
2025-12-20

Tags: [[Computer Architecture]]
# CPU Data Path
Instruction Processing Steps:
1. **Fetch** Instruction from memory, this stage is also responsible for reading the next instruction from memory and then incremented the **PC**, or program counter, so that it points to the next instruction in memory.
2. **Decode** the instruction and generate control signals
3. **Execute** the instruction
4. read or write the instruction to **memory**
5. **Write Back** results into the register file

**Single Cycle Data Path:**
- In this version we ensure that every instruction finishes within a single clock cycle, ensuring that each instruction operates independently.
- One downside is that we need multiple of the same components since we can't reuse them.
- Single cycle data paths aren't time efficient since they are restricted by the slowest instruction, load word in mips

**Performance:**
- CPU Execution time= Instruction count x CPI x Clock Cycle time
- Performance = 1 / CPU Execution Time
- The Iron Law:
	- Time = Seconds/Program = Instructions/Program $\cdot$ Clock Cycles/Instruction $\cdot$ Seconds/Clock Cycles

**Problems with a Single Cycle Data Path**
- Longest delay determines the clock period (critical path)
- Not feasible to vary period for different instructions due to complexity, unreliability, and noise concerns
- Violates the principle of making the common case fast
- Can be improved with pipelining
### Control Bits
These are used for higher order processing, there are different routes for say a `sw`, `lw`, `add`, or a jump so we use the control bits to properly route all instructions. Below are some commons ones that might show up.
![[Pasted image 20251220174858.png]]
![[Pasted image 20251220174905.png]]
![[Pasted image 20251220174936.png]]

# References
- [[MIPS ISA]]
- [[Pipelining]]
- For more see EECS 645 lectures ~ 10-14