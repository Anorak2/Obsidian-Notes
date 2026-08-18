
2026-07-17

Tags: [[Data Structures]]
# AVL Trees
An AVL tree is a form of self balancing binary tree, that for each node enforces that the balance factor can't differ by more than one. AVL Trees are particularly useful when you need frequent and efficient lookups, like in database indexing, memory-intensive applications, or where predictable time complexity is crucial

Balance Factor = left subtree height - right subtree height
For a Balanced Tree(for every node): $-1 \leq$ Balance Factor $\leq 1$

In order to re-balance themselves, AVL trees use rotations since they can be performed in constant times. Insertions are followed by checks up the tree to ensure that balance is maintained but for deletion multiple rotations may be required, which Red-Black Trees manage better.

**Vs Red-Black Trees**
AVL Trees are able to provide faster lookups, but might run with more overhead on insertions and deletions since balancing is more strictly enforced.

# References
- [[Tree*]]
- [[Red Black Trees (LLRB)]]