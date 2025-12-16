
2024-12-30

Tags: [[Programming]] 
# Dynamic Programming
The main idea here is to store the solutions to sub-problems so that we only need to solve each sub-problem once. To solve DP problems what we do is write a recursive problem in a way that there are overlapping problems.

To make sure that a value is only computed once we store the results of calls either top down (memoization) or bottom up (tabulation)

**When to use**
1. Optimal substructure. This means that we use the optimal results of subproblems to achieve the optimal result of the bigger problem. For example when we're doing [[Graphs Shortest Path Problem - Dijkstra's|Dijkstra's algorithm]] we also need to find the path to every intermediate value between the source node and the destination node.
2. Overlapping subproblems: This is when we need to repeatedly solve the same problems, for example the Fibonacci problem we need to calculate n-1 and n-2 to calculate n, and so on.

**Approaches**
1. Top Down (memoization). This is when we solve the recursive problem and then add a memoization table to avoid repeatedly calling the same subproblems. This way before solving a problem we can check if the table already has a solution for it.
2. Bottom-Up (tabulation). This is where we start with the smallest sub problems and build our way up to the larger problems
	1. We write an iterative solution and build it in a bottom up manner
	2. We use a DP table where we first fill in the base cases and then fill in the remaining entries according to the formula
	3. We only use recursion on table entries and do not make recursive calls
# References

