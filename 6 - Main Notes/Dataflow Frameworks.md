
2025-09-29

Tags: [[Software Security Evaluation]] [[Data]]
# Dataflow Frameworks
![[Pasted image 20250929155208.png]]
- Mark each block to indicate all possible values coming into that program point
- Mark each edge to indicate all possible values coming out of that point

## Potential
Dataflow graphs have a relatively straightforward computation: update the dataflow fact stored at each basic block boundary until saturation

In our examples, output was always…
- Complete behavioral over-approximation -> no behaviors missed
- Relatively precise -> few “false positive” behaviors
- Saturated -> terminated

We’d like some stronger guarantees:
- Guaranteed termination
- Amenable to chaotic iteration
- Some degree of precision

more formally:
- A fact datatype (ideally of unbounded size)
- An ordering that indicates progress
- Unique Solution
- A guarantee of a finite number of steps to hit the maximum value 
- An update step that never loses progress

**Chaotic Iteration:** A worklist algorithm that selects the next worklist item in any order and necessarily assumes some sort of progress towards the goal. Since we can reach "uncomputed" sets chaotic iteration assumes a reasonable "initial" value.

# Practical Considerations
We have guarantees we'd like to extract from our analysis engine:
- Termination
- Completeness (of analysis)
- Precision (repeatability)

To accomplish this we need:
- Over approximate, monotonic update functions
- A finite height, complete lattice 

**Semantic Gap:** "The difference between descriptions of an object by different linguistic representations".


# References
[[Control Flow Graphs (CFG)]]
