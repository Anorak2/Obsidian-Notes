Tags: [[Databases]] [[Data]]
# Functional Dependencies

Functional Dependencies describe the relations between attributes, with one attribute determining in some way what the other value is.

- FD's are constraints like keys
- FD's are actually "keys" for a certain subset of columns
- Database design based on [[Normalization|Normal Forms]] require collecting all of the FD's before we start

**Legality**
An instance that satisfies all of the real world constraints is considered a **legal Instance**, and appropriately a legal instance requires all functional dependencies to be legal.

**Trivial FD's**
Some FD's are considered trivial, for example $A \to A$. However there are other types, general an FD is considered trivial if its of the form $\alpha \to \beta$ and $\beta \subseteq \alpha$ 

**Closure, called $F^+$**
We say that a set is closed if all of the relations in a schema "connect" to eachother with functional dependencies if we start from just one attribute. We compute this using the [[Armstrong Axioms]] 
R = (<u>A</u>, <u>B</u>, C, D)

**Finding Keys**
To find a key using FD's we start by creating a list of elements that are on the left side, and elements that are on the right side. We want to start with the left hand side elements, and specifically elements that are only on the left hand side. If we generate the closure of these elements and they close, then we're done, but if that isn't the case then we have to keep adding elements to the key until it closes.

# References
[[Normalization]]