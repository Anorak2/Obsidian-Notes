
2026-03-18

Tags: [[Databases]]
# The Normal Forms
Normalization is a systematic way to organize data, minimize redundancy, improve data integrity, and simplify data maintenance. One such benefit is that by having no data duplication the state across the database is trivially consistent. However normalization comes with trade offs, this includes having an increased number of tables which can lead to slower queries. This is due to the data being "chopped up" into many to one relationships between queries, which has to be reassembled in order to be of use.

**Requirements**
To do normalization we need to know the primary key, and the functional dependencies between relations. The reason why is the primary key is kind of the basis for examining a relation, and FD's determine the relationships between attributes.

Generally when designing a database, we'd like for our data to be in either 3NF or BCNF
### First Normal Form (1NF)
The first normal form requires that all table column entries are atomic, which means no lists etc. All further forms of normalization require 1NF
### Second Normal Form (2NF)
Requirements:
- schema is in the the first normal form
- also every non-prime attribute must be dependent on the entire primary key

**This means no partial dependencies**: no attribute that isn't part of a candidate key (non-prime), should be [[Functional Dependencies|Functionally Dependent]] on only part of the primary key

**Full functional Dependency on the entire key** all non prime attributes must depend on the entire key

### Third Normal Form (3NF)
Requirements:
- schema is in the second normal form
- No transitive dependencies 

This means that we can't have dependencies like R(<u>A</u>, B , C) $B \to C$ since B is not a part of the key. Or put another way, no non-key attribute can depend on another non-key attribute

**Alt definition**
A relational schema R is in 3NF if whenever $X \to A$ holds in A, either
- X is a key of R, or
- A is a prime attribute of R
### Boyce Codd Normal Form (BCNF)
Requirements:
- A schema is in the third normal form
- Whenever $X \to A$ is a functional dependency that holds in R and $A \not \in X$ then    X is a key for R

BCNF is very similar to 3NF, but of course it is a stronger version.
# References
- [[Normalization]]
- [[Functional Dependencies]]