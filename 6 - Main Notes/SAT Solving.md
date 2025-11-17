
2025-11-16

Tags: [[Computer Science]] [[EECS 677 - Software Security Evaluation]] [[Math]]
# SAT Solving
![[Pasted image 20251116231830.png]]
As a brief overview P=NP is about a class of problems NP here a solution can be generated in polynomial time by a nondeterministic [[Turing Machines|Turing machine]] and a solution can be verified in polynomial time by a deterministic turing machine.

**NP-Completeness**
This is the class of problems where a solution could be used as a solver for any problem in NP. SAT is the canonical example of an NP-complete problem.

**Conjunctive Normal Form**
Each clause can have 1 or more literals, 0 or more negations, and 0 or a disjunction. What is nice is that any boolean expression can be represented as a conjunction of disjunctions using the standard Boolean transformations.

![[Pasted image 20251116232504.png]]

## Strategies
---
**Unit Propagation**
a literal that exists all alone in a clause with only one literal is a unit. To do unit propagation means that if we have a literal on it's own then it **must** be true if there is a satisfying assignment. Similarly if a clause is negated on it's own then it **must** be false if there is a satisfying assignment.

**Pure Literal**
If a variable exists with only one polarity, either always true or always false, then it can be called pure. Due to the nature of a pure literal if we make it true (or false if negated) then we **cannot** regret this choice while searching for a satisfying assignment.

**DPLL**
![[Pasted image 20251116233048.png]]
Essentially:
- if it is trivially true or false return the function
- unit propagate as much as possible
- pure literal assign as much as possible
- brute force

# References
[[P=NP?]]

[[Symbolic Execution]]

[[Concolic Execution]]

[[Turing Machines]]