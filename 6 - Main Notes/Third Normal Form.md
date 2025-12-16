Tags: [[Databases]]
# Third Normal Form

3NF requirements
- [[Second Normal Form]]
- No transitive dependencies

This means that we can't have dependencies like R(<u>A</u>, B , C) $B \to C$ since B is not a part of the key. Or put another way, no non-key attribute can depend on another non-key attribute

**Alt definition**
A relational schema R is in 3NF if whenever $X \to A$ holds in A, either
- X is a key of R, or
- A is a prime attribute of R

# References
[[Normalization]]

[[Second Normal Form]]

[[Functional Dependencies]]