
2025-11-16

Tags: [[Software Security Evaluation]] [[Dynamic Analysis]]
# Concolic Execution
Concolic Execution is about enhancing the abilities of Symbolic execution. The fundamental difference is that as soon as symbolic execution hits even a single syscall it might encounter so much state that it never returns. Concolic Execution is an attempt to fix this, with the word literally being a combination of concrete and symbolic. The big idea is that at some point we replace the symbolic value with a concrete value so that we can get increased coverage (at the cost of completeness) and it can still pair with termination thresholds. 

**Scope and Limitations**
- Overburdening the solver
	- At some point, the path constraint becomes unwieldy

- There may be code outside the analysis engine
	- What happens on a network call?

The reality is that at some point we just guess and pick a random value

**Klee**
Klee is an actual concolic execution engine
# References
[[Symbolic Execution]]

[[SAT Solving]]

[[SMT Solving]]