# Old
```
opt -dot-cfg prog.ll > /dev/null
opt -passes=dot-cfg prog.ll > /dev/null
```

State space is the set of all possible configurations of the target model

Naive State space representation is when we consider every possible paths of the program, which for n bits of memory is 2^n


The elaborate idea is to check every path in the program one by one but this is bad since it's incredibly expensive; the number of paths will grow exponentially with every branch. Even then, there is no guarantee that every path has been properly checked.

**Modeling Values:**
What we can do instead of over representing values is say $x = \{1\}$, or that x can equal a set of values. This makes it way easier since if $x = \{0, 1, 2\}$ and $y = 4/x$ then we can definitively say there is a potential divide by zero error. We also have to do exhaustive transforms when we reach something like a multiplication. But by doing this now we can solve the problem of many program configurations on even a single path

**Meet Over all Paths**



# Lecture 11

**Exercise 11**
```Recall that the set of English words, ranked by substring inclusion, forms a poset but not a lattice. Explain why and give an example```


Reflexive: Every word includes the substring of itself

Anti-Symmetric: if two words include substrings of each other, they must be the same word

transitive: if a is a substring of b, and b is a substring of c, then a is a substring of c


Lattices also impose a least upper bound, so if there are the words "a" and "he" they have no greatest lower bound or least upper bound.

**Quiz 1** will be next Friday, 9/18. Quizzes are non-overlapping. Everything from the first lecture up to Monday's (9/8) lecture.

## Dataflow Frameworks
the main thing is that we're going to mark each block to indicate all possible values coming into that program point, and mark each edge to indicate all possible values coming out of that point. Compute until all annotations at a fix-point. 

**Abstract Interpretation**
The abstract domain of summary values, transfer functions and edge merging in the abstract domain

**Code is necessarily flawed**. If it wasn't analysis is pointless, analysis is also code

## Formalizing Dataflow
Classic Pitfalls we need to consider:
- Non-termination (halting problem)
- Trivial Solutions
- Incomplete Solutions

Formal Tools:
- A structure to abstract values (a complete lattice)
- An update function that always makes progress (monotonically non-decreasing)
- an algorithm that never ignores behavior (least fixpoint over-approximation)

Intuition:
If we can rank all possible (abstract) values then we can insure we're always making progress, or if we aren't then we are at a fixpoint.

Formal (ish) requirements for the right tools
- A fact datatype (ideally unbounded in size)
- an ordering that indicates progress
- Unique Solution
- A guarantee of 

Throwback: Hasse Diagrams. A Hasse diagram is a drawing of the transitive reduction of a partially ordered set. Implied transitive relations, implied reflexivity.

A function f is a monotonic function if $x \subseteq y$ implies $f(x) \subseteq f(y)$. An element z is a fixpoint of f iff z = f(z). Example: $glob(x) = x \cup \{ b\}, glob(\{b\} \to \{b \}$ is a fixpoint of glob. $glob(\{a\}) \to \{a, b\}$ is not a fixpoint. glob(glob(any set)) is a fixpoint of glob, as well as glob($b \subseteq$ any set).

Practical bonus: if L is a complete lattice and f is monotonic, then f has a greatest fixpoint and a least fixpoint. IF L has no infinite ascending chains, the least fixpoint can be compute by iterative application of f so that the analysis **will** terminate.


## Generalizing Analysis
We end up with a plug and play analysis where we can apply a generalized update function on a lattice.

**Chaotic Iteration** 
This is a worklist algorithm
- Select the next worklist item in any order
- Necessarily assumes that we progress towards some goal

When dealing with uncomputed sets we assume a reasonable "initial" value

**Precision vs Efficiency trade offs**
With a complete lattice we can eventually terminate, and with a small lattice we can terminate faster. The shallower the lattice, the faster we can make a fixpoint. We can also set a hard limit on the lattice size and have a hard limit on the runtime.


We now have
- Completeness of bug finding and soundness of verification

# Lecture 12
## Terms
A security incident workflow has a:

threat actor -> (exploit) -> attack vector -> (malicious behavior) -> security impact 

**Threat Models**
- Set of adversary goals
- Set of adversary capabilities

**How do bad programs run?**
Reactive Concerns, evaluation others programs
- Social Engineering
- "Flaws" in system installation policies

Proactive Concerns, evaluating out own program
- The program accidentally does damage
- the program contains a vulnerability


Data and code share memory, and code **is** data. the good and bad of this is that programs can write code just like any other form of data.


## 9/22
A source operation is an operation that generates data
a sink operation is an operation that consumes data
a flow is a program path segmenet that begins at a source and ends at a sink