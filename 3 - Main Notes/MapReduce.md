
2026-07-13

Tags: [[Databases]] [[Data Systems]]
# MapReduce
MapReduce is a programming model that uses parallel architecture to speed up large scale data manipulation and querying. It exists somewhere between a declarative language like SQL and an imperative language.

In practice this means writing two functions, specifically Map and Reduce. The Map function is called on the document and it collects any relevant data before handing it off. This data goes to the Reduce function which performs some operation on the data in order to aggregate or "boil-down" this data. 

These functions also do have restrictions placed on them, they can only use the input parameters and must not have any side effects. This restriction makes the task simply parallelizable, and thus the DB is able to run them in any order, and rerun them if there is a failure. This restriction is a boon, since the functions can still make library calls, parse strings, or perform complicated logic.1


# References
- [[Languages]]