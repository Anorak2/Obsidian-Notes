
2025-09-29

Tags: [[Software Security Evaluation]] [[Math]] [[Computer Science]]
# Lattices
A lattice is a [[Poset]] in which each pair of elements has:
- A least upper bound (the join)
	- for x and y, the join z is defined such that for all w such that x ⊆ w and y ⊆ w, w ⊇ z
		- x ⊆ z and
		- y ⊆ z and
- A greatest lower bound (the meet) basically the same as least upper, but reversed

A complete lattice is a lattice where all subsets have a meet and join

## Examples:
![[Pasted image 20250929153439.png]]
I usually think of a lattice as requiring a set of unique values, and a clear ordering which shows greater than or less than for each value.

## Why?
If a function can be represented as a complete lattice then we can ensure that there is a greatest and least fixpoint (z = f(z)). If L has no infinite ascending chains, the
least fixpoint can be computed by iterative application of f. The first is beneficial because every finite lattice is a complete lattice, and the second means that every analysis will terminate.
# References
[[Poset]]
