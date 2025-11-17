
2025-11-16

Tags: [[EECS 677 - Software Security Evaluation]] [[Computer Science]]
# Points To Analysis, Anderson's and Steensgard's
The problem currently is that approaches such as RTA fail to consider multiple functions together leading to unsound analysis. By considering pointers across multiple functions we seek to help remedy that. First though we have to acknowledge that finding pointsTo sets is expensive and that inter-procedural analysis and flow sensitive analysis are out of scope, so Drew chose to focus on flow insensitive algorithms.

## Anderson's Analysis
---
![[Pasted image 20251116192941.png]]
Anderson's analysis is a flow insensitive analysis where each statement adds a constraint over the points-to sets and we end up with a solvable system of constraints.

**In Practice:**
![[Pasted image 20251116193218.png]]

**Overhead**
In the worst case this analysis will take Cubic time which is not good, we can help address this by eliminating cycles. To eliminate cycles we have to detect them and then collapse them in the points-to relation.

## Steensgard's Analysis
---
![[Pasted image 20251116194009.png]]

To address some of the drawbacks we remember that **Simpler abstractions reach fix-points faster**. Steensgard's Analysis is an alternative form of analysis that aims for near linear time points-to analysis by helping us reduce our search space. 

To do this we do away with the notion of subsets and introduce equality constraints where we declare two variables functionally equivalent. This means that nodes can only point to one other node, and that if a node ever points to two nodes we merge both of those nodes.
![[Pasted image 20251116193924.png]]

**Ex:**
![[Pasted image 20251116194120.png]]



# References
[[CHA and RTA]]

[[Dataflow Frameworks]]