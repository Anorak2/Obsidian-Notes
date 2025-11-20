
2025-11-16

Tags: [[EECS 677 - Software Security Evaluation]] [[Computer Science]]
# SMT Solving
SMT, or Satisfiable Modulo Theories, is where we call out to specific theories in order to find satisfying assignments. One reason we might do this is to concertize specific states in Concolic execution since a program won't accept $\alpha$.

**Theory Solvers**
> The individual solvers are the bread and butter of SMT solving

- Theory of equality on uninterpreted functions
	- There are some things about a function that we just automatically know, for example a function must take some amount of arguments and produce an output otherwise it isn't a function.
	- 
- Theory of linear integer arithmetic
	- (0, 1, +, -, $\leq )$ interpreted over $\mathbb{Z}$      
- Theory of arrays
- Theory of strings
- Theory of bit vectors

**QFOL: Quantifier-Free First Order Logic**
Goal: Break down the constraint system to match our core logical theory at the top level, with individual clauses potentially in our theory signatures.

Logical Symbols:
- Parenthesis
- Propositional Connectives (and, or, negation, implication, bi-implication)
- variables
- ~~quantifiers~~ this means for all and there exists
Non Logical Symbols:
- Equality
- Functions: +, -, %, & bitwise, f(), concat...
- Predicates: is_substring...
- Constant Symbols: 1, 0, null, ...

**EUF Axioms**
- Congruence
	- $x = y = f(x) \implies f(y)$ 
- Symmetry
	- $x = y \implies y = x$ 
- Transitivity
	- $x = y \land y = z \implies x =z$ 
- ...

**Blocking Clauses**
Something to note is that sometimes even if all of our clauses look right and DPLL is able to return a satisfying solution it may still not be valid. In this instance we just need to add in an additional clause blocking that incorrect solution.
# References
[[SMT Solving]]

[[Concolic Execution]]