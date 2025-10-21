
# Basic
Every function has a two sections, the declarations and the predicates. Z works by combining set theory, where we model data as sets, and predicate logic to define clear rules.

![[Pasted image 20251003141251.png]]
Hello world example

| Function    | Syntax                             |
| ----------- | ---------------------------------- |
| Conjunction | $S \land T$                        |
| Disjunction | $S \lor T$                         |
| Difference  | $S \space \textbackslash \space T$ |
| Overriding  | $S \oplus T$                       |
**Functions and Relations**
- Relations Sets of ordered pairs, e.g., (x,y)  
- Element mapping x ↦ y shows x maps to y  
- Domain (dom) set of all elements on the left side of the mapping (the inputs) 
- Range (ran) set of all elements on the right side of the mapping (the outputs)  
- Partial functions: Each domain element maps to at most one range element


**Variables**
- Input variables: An input variable, a value to an operation, is shown with a question mark (e.g., name?)
- Output variables: An output variable, a value produced by an operation, is shown with an exclamation mark (e.g., name!)
- Postcondition variables: The state of a variable after an operation is shown with a prime symbol (e.g., name').

**Approach**
- Establish foundations: Define basic sets (e.g., Users, Passwords)
- Define initial state: Use schemas with sets, functions, and relations
- Define operations: Set pre- and post-conditions for each action
- Verify with proof: Prove theorems to confirm correctness
![[Pasted image 20251003142419.png]]
*U* is the universal set - the set of all of the elements from which a given set is drawn.
$\varnothing = \{\}$
if all of the elements of a set S are also elements of set T then it is a subset
if S is a subset of T, and S is not equal to T, then S is a proper subset

**Cardinality**
written as $|A|\text{ or } \#A$

**Power Set**
This is the same as making a set with every possible combination from the original set. It will have a cardinality $2^n$ elements more than that of its base.


