Status:

Tags: [[Database]]
# Normalization

Normalization is a systemic process that formally helps organize data, minimize redundancy, improve data integrity, and simplify data maintenance.

There are many types of normalization, with the most important being the [[Third Normal Form]] and [[Boyce-Codd normal form]]. Normalization is a set of rules that a database could follow, with each successive layer being a little more restrictive but also creating a more robust database that is less likely to have issues like duplication of data. Generally our goal is to get a relationship to be in either [[Third Normal Form|3NF]] or [[Boyce-Codd normal form|BCNF]].

**Requirements**
To do normalization we need to know the primary key, and the functional dependencies between relations. The reason why is the primary key is kind of the basis for examining a relation, and FD's determine the relationships between attributes.

# References
[[First Normal Form]]

[[Second Normal Form]]

[[Third Normal Form]]

[[Boyce-Codd normal form]]
