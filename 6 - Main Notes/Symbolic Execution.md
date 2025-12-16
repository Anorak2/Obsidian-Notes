
2025-11-16

Tags: [[Software Security Evaluation]] [[Dynamic Analysis]]
# Symbolic Execution
Dynamic analysis is great, but as mentioned in some previous notes it has a significant coverage problem. So what if instead on every path we explored both options? 

The big idea behind symbolic execution is that we keep track of what a variable's possible values could be at any given point, respecting any branches in the code. for example if we had a structure like `if(var < 10) thing; else thing2;` then we would have to remember `var < 10` inside the if and that `var >= 10` inside of the else.

**SAT**
Something very notable about symbolic execution is that we end up with a system of boolean constraints and that we will need to check if there is a **sat**isfying assignment meaning that the code is reachable. This problem is very famously [[P=NP?|NP-hard]]

``` Symbolic_Algorithm
At each line of the program:
• Advance a symbolic program state
• When you hit a branch split the symbolic state into 2 versions
	• 1) a state that satisfies the predicate
	• 2) a state that does not satisfy the predicate
```
# References
[[Dynamic Analysis|Test Cases]]

[[SAT Solving]]

[[SMT Solving]]

[[P=NP?]]