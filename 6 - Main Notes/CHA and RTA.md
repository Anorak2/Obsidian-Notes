
2025-11-16

Tags: [[Computer Science]] [[EECS 677 - Software Security Evaluation]] [[Security]]
# Class Hierarchy Analysis and Rapid Type Analysis
---
Previously we talked about [[Mod-Ref Analysis|Mod/Ref Analysis]] but the problem is that for situations more complex than globals only our analysis can become tricky very quickly. **Class Hierarchy Analysis** is where in an object oriented language we create the inheritance tree. Notably in CHA we use a "safe over-approximation" where we include all defined classes whether or not they are used. **Rapid Type Analysis** is a refinement on CHA where we consider only initialized classes and consider only reachable code.

``` RTA-Algorithm
RTA = call graph of functions (initially edgeless)
CHA = call graph via class hierarchy analysis
W = worklist
W.push(main)
while not W.empty:
	M = pop W
	T = allocated types in M
	T = T U allocated types in RTA callers of M
	foreach callsite(C) in M
		if C is statically-dispatched:
			add edge C to C’s static target
		else:
			M’ = methods called from M in CHA
			M’ = M’ intersect functions declared in T or T-supertypes
			add edge from M to each M’
			W.pushAll(M’)
```

This is all well and good but **RTA** is actually an **unsound analysis**. In the image below RTA will not include an edge from bar to `toString` because neither bar or its callers (main) allocated any instance that `toString` could be called on.
![[Pasted image 20251116192030.png]]
# References
[[Mod-Ref Analysis]]