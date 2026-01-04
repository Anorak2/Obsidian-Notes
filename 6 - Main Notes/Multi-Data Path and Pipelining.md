
2025-12-20

Tags: [[Computer Architecture]]
# Multi-Data Path and Pipelining
As mentioned in the [[CPU Data Path|data path]] note, single cycle data paths kind of suck because they are slow and costly. We can help fix this by introducing a multi-cycle data path, in this version we shorten the clock cycle and only have one of each major component. We set the clock cycle so that one component process can be done inside of a cycle, rather than an entire instruction. One example would be fetching the instruction on one cycle, decoding it on another, then performing an ADD operation on the third cycle, etc.

**Pipelining:**
Once we've broken out the instruction into independent segments, something you might notice is that often components are idle in a predictable way. A good analogy is washing, drying, and folding clothes; While one set of clothes is drying you can start another in the washer, this is equivalent to pipe-lining.

![[Pasted image 20251220181641.png]]

**Forwarding:**
- Forwarding allows for us to use a result immediately after it is computed, for example allowing us to pass a result from the Ex stage of one instruction directly to the ALU so it can be used for calculating the result of the next instruction.
- This doesn't work for everything, since we can't forward a load-use dependency for example.
- A `NOP`, or a stall, can be used to generate correct results regardless. These slow down the program but are sometimes required to get correct results, although an intelligent compiler can rearrange instructions in order to limit stalls.
# References
- [[CPU Data Path]]
- [[Pipeline Hazards]]