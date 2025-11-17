Status: 

Tags: [[Algorithms]] [[Open Problems]]
# P=NP
P=NP Is based around the idea that we can have Efficiently Solvable problems (p), and problems for which a "yes" answer is efficiently verifiable (NP). Specifically the question at hand is whether the set of set of non-polynomial problems with a polynomial amount of information can be reduced to a polynomial runtime.
![[Pasted image 20251116231729.png]]



## Implications
---
What is interesting is that every singly polynomial problem can be reduced to 3SAT. This means that **for any decision problem for which a yes answer can be efficiently verified can be reduced into a 3SAT problem**. This transformation is also efficient.

The question is, are all NP problems also P problems. Or in other words, are all problems with efficiently verifiable solutions also efficiently solvable?

What is cool is that there are tons of NP complete problems that can all reduce into eachother, and thus solving any of these problems means that you solved all of them. These are known as NP complete problems and there are tens of thousands of them.

**Fun Fact!**
All Math proofs are in NP, for example to check if the Riemann hypothesis is true all we need to do is verify the proof. If P=NP then mathematical proof can be automated, so if P=NP then we might be able to trivially solve many other problems.

# References