
2025-01-08

Tags: [[Computer Science]] [[Math]] [[Algorithms]]
# Recurrence Relations
A recurrence is an equation or inequality that describes a function in terms of its value on smaller inputs. A recurrence is very useful for many different scenarios, for example a recurrence relation that describes Merge Sort in terms of Big O notation.
$$
T(N)=
\begin{cases}
	\Theta(1) & \text{if }n=1 \\
	2T(n/2) & \text{if }n>1
\end{cases}
$$
This recurrence simplifies to $\Theta(n \space \log n)$, but recurrences can take many forms and they are primarily useful for describing divide and conquer algorithms.

**Solving Recurrences**
There are three main ways to solve a given recurrence;
- The substitution method is where we guess a bound and use mathematical induction to prove our guess is correct
- The recursion tree method converts the given recurrence into a tree whose nodes represent the costs for various levels of recursion.
- The master method provides recurrences for the form $T(n)=aT(n/b)+f(n)$ where $a \geq 1, b > 1,$ and $f(n)$ is a given function


## The Substitution Method
1. Guess the form of the solution
2. Use mathematical induction to find the constants and show that the solution works

Unfortunately there is no general way to make a good guess for the correct solutions to recurrences. Generally it just takes some intuition, creativity, experience, and some luck. Of course if there is a recurrence similar to one you've seen before that is a great starting point.

See page 87 for exercises.
## The Recursion-tree Method
Sometimes coming up with a good guess can be really hard, even though if your guess is right you can relatively easily prove it's true. In a recursion tree each node represents the cost of a single sub problem somewhere in the set of recursive function calls. This method is best used to generate a good guess which can then be verified using the **substitution method**, though if you are very careful in drawing and summing a recursion tree can be used directly for a proof.
![[Pasted image 20250520001558.png]]



# References
[[Merge Sort]]