Status: 

Tags: [[Database]] [[Data Structures]]

# BCNF
Requirements:
- A schema is in the [[Third Normal Form]]
- Whenever $X \to A$ is a functional dependency that holds in R and $A \not \in X$ then    X is a key for R

BCNF is a stronger form of 3NF since it requires a relation to already be in 3NF, and generally our goal is to have each relation in either BCNF or 3NF

# References
[[Normalization]]