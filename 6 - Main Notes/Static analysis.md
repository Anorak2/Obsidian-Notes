
2025-09-29

Tags: [[EECS 677 - Software Security Evaluation]]
# Static analysis
Static analysis is the process of reviewing code without running it, the simplest version is to just look at the code.  

**Basic Idea:** Dataflow analysis can be adopted for checking a variety of security / correctness properties such as leak detection, vulnerable state detection,  and program understanding

**Benefits:**
- "Analyst's Sieve" It allows us to sift out programs such that everything left is a definitely good program.
- Non-Interactive
	- It can run in the background and by using abstractions we don't need inputs

**Practical Issues / Limitations:**
- It is unsound for bug finding and incomplete with program verification
- Scalability
- Significant engineering effort
- findings may not be easily actionable
# References

