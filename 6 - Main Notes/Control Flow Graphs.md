
2025-09-29

Tags: [[EECS 677 - Software Security Evaluation]] [[Computer Science]]
# Control Flow Graphs
> A control flow graph is graph representation of all possible paths through a program during its execution
> ![[Pasted image 20250929150907.png]]


## Building the CFG
Generally building the CFG is an iterative process where we pass over instructions and mark the leaders and terminators of each block or create new ones if necessary. We keep doing that until no more leaders/terminators are found and then we define code blocks based on these boundaries. We then connect the sources to the destinations (EG function calls for example) and then refine based on analyses.

Furthermore we also introduce the restraint of **Hammocks**, this means that every code block must have exactly one entry point and one exit point. In practice we also have special kinds of link edges for call sites and function returns / exits.

## Fixing issues with CFG's
The main problems are as follows:
- **Value Uncertainty:** To fix one of these problems we can represent data as a value set, so if we have a variable x at a certain point in the CFG the value set could be {0, 1, 2, 3, 5, 8}. The problem is that this can be very difficult, tedious, and even easy to get wrong.
- **Unbounded Paths:** It is simply impractical to try and consider every possible path through a CFG independently since as the CFG grows the state space increases exponentially. Furthermore, even on the same path the state can vary wildly.
- **Cyclic Dependencies:** The problem is that loops can be very difficult due to circular dependencies and potentially unpredictable number of runs. This also runs into the halting problem.
- **Tedious Saturation:** When we have a cyclic dependency it becomes very difficult to know when to stop, at what point is "good enough" (saturation) for the program


### Abstracting Data:
Instead of individually storing each value that a variable could hold, instead we can simplify into a couple of different placeholder sets. Often we use just four:
- $\gamma(zero) = \{0\}$ 
- $\gamma(pos) = \{\text{all positive ints}\}$ 
- $\gamma(neg) = \{\text{all negative ints}\}$ 
- $\gamma(num) = \{\text{all ints}\}$



# References
[[Graphs]]

[[The Halting Problem]]

[[Lattices]]
