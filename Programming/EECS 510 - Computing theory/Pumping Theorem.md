
[[Theory of Computing]]

This is a very important relationship for [[Regular Languages]] that effectively states for any sufficiently long strings in a language they have to be pumped, which means having a middle section repeated an arbitrary number of times.

This is actually very intuitive when looking at the formal definition of a regular language, since Kleene star is allowed by definition.

**DEFINITION**
For any infinite [[Regular Languages|regular language]], $Y$, there is a positive number, $p$, such that for every string s where $s \in L$, which has a length of at leas p, we can partition the string as $s = xyz$ (broken down into three pieces)

and the following hold:
- $|y|$ is the number of states in the minimal DFA
- $|xy| < p$ is non-empty because any cycle has at least one edge
- $(\forall n \geq 0)(xy^nz \in L)$

This means for any string that is long enough in a language, we can break it down into three sections with the middle expression being repeated 0 $\to$ n times, with each value of n also being in the language

**PROVING NON-REGULARITY**
To prove non regularity with the pumping theorem, we usually take the following form.
for the language $a^nb^n$ 
- We can assume that there is some constant value p as required by the pumping theorem
- We can take a string $a^pb^p$ and decompose it into parts x, y, and z
- $|xy| \leq p$ 
- we know that y must appear within the first p symbols since it must represent the start of the cycle
- since we know $|xy| \leq p$ we know that the string y consists of only a's
- since $|y| \geq 1$ it cannot have a length of 0
- if we pump y we get $xy^2z$ we get a string which isn't in L, since the a's and b's must match therefore L cannot be regular 