
2025-02-17

Tags: [[Algorithms]] [[Computer Science]]
# Master's Theorem
When we are categorizing algorithms it can be difficult to find the runtime complexity for recursive algorithms. We can however easily express recursive algorithms in terms of a [[Recurrence Relation]].

This specifically works for recursive relations of the form:  $T(n) =aT(n/b) + \theta(n^k\log^pn)$

Here:
	a is the number of subproblems in the recursion and a >= 1
	 n/b is the size of each sub problem
	 b > 1, $k \geq 0$, and p is a real number

| Cases | Description                                                                          | Master Theorem Bound                            |
| ----- | ------------------------------------------------------------------------------------ | ----------------------------------------------- |
| 1     | Works to recombine a problem with a bunch of sub-problems, like if it was leaf heavy | if $a > b^k$, then $T(n)                        |
| 2     | Work to split/recombine a problem that is comparable to subproblems                  | Then $T(n) = \Theta(n^{c_{crit}}(\log n)^{k+1}$ |
| 3     |                                                                                      |                                                 |
|       |                                                                                      |                                                 |
| 2a    |                                                                                      |                                                 |
| 2b    |                                                                                      |                                                 |
| 2c    |                                                                                      |                                                 |

# References

