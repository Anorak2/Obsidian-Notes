
2025-09-29

Tags: [[Software Security Evaluation]] [[Data]]
# Domination and Control Dependence Graph
The problem we are having is that a line of code very often depends on the lines of code that executes before it, and visualizing this can be tricky. To deal with this we introduce several terms that relate to the interactions between code blocks.


**Post Domination:**  PDOM(X,Y) <-> Paths to Y must go through X
you cannot get to y without going through x
> X guards the path to Y

**Forward Domination:** FDOM(X,Y) <-> Paths from X  must go through Y
> Y is guaranteed to be in the future of X

**Control Dependence:** Y CD x <-> there is a CFG path from X to Y omitting IFDOM(X)
> it's possible to get from X to Y but it's not guaranteed

**Data Dependence:** Domination is more than control, it’s also what values mattered to your behavior
# References
[[Control Flow Graphs (CFG)]]

