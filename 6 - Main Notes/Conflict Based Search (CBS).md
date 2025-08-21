
2025-04-13

Tags: [[Algorithms]] [[High Performance Computing]] [[Computer Science]]
# Conflict Based Search
Conflict based search in it's vanilla form is a way to solve [[Multi Agent Path Finding (MAPF)|MAPF]] optimally using a two layer search. The higher level performs a best first search on a binary constraint tree (CT) where each CT node N contains a set of constraints that are used to coordinate agents and avoid conflicts.

**How it works:**
The root CT node contains an empty set of constraints and a set of shortest paths. When expanding a CT node, CBS checks for conflicts among its paths. If there are none, then the CT node is a goal CT node, and CBS terminates. Otherwise, CBS chooses one of the conflicts and resolves it by splitting the CT node into two child CT nodes. In each child CT node, one agent from the conflict is prohibited from using the conflicting vertex or edge at the conflicting timestep by way of an additional constraint. The path of this agent does not satisfy the new constraint and is replanned with A* on the low level. CBS guarantees completeness by eventually exploring both ways of resolving each conflict. It guarantees optimality by performing best-first searches on both its high and low levels


# References

