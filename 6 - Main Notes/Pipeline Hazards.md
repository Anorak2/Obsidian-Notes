
2025-12-23

Tags: [[Computer Architecture]] [[Performance Measurement & Reliability]]
# Pipeline Hazards
Something you may notice about pipelining is that sometimes instructions overlap in dangerous ways, it's easy to imagine a situation where the next instruction depends on the previous instruction resulting in an inaccuracy. This is what we call hazards, or situations that prevent the next instruction from starting in the next cycle. There are three general kinds of hazards
- Structural hazards where a resource is busy. Ex a load and store with single memory access
- Data hazards where we need to wait for the previous instruction to finish it's read/write. There are three types, a read after write (`RAW`), a write after read (`WAR`), and write after write (`WAR`)
- Control hazards where deciding on a control action depends on a previous instruction

# References
- [[CPU Data Path]]
- [[Multi-Data Path and Pipelining]]

