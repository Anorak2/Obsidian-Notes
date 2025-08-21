
[[Theory of Computing]]

**Definition**

A non-deterministic finite automata (NFA) is a  [[Finite State Machines]] consisting of the following:

- $Q$, a set of states, one of which is the initial (or start) state, and a subset of which are final (or accepting) states.
- $\Sigma$, an alphabet of valid input symbols
- $\delta: Q \times(\Sigma \cup \lambda) \to 2^Q$, a function which, given a state and an input symbol (which could be $\lambda$), determines the next possible set of states of the machine to move to (i.e. a choice of states)

$2^Q$ is sometimes written as $P(Q)$, which is the power-set of the set of states, $Q$.

The power-set of a set is this set of all possible subsets of that set

If $Q = \{q_0, q_1\}$
$2^Q= \{ \varnothing, \{q_0\}, \{q_1\}, \{q_0, q_1\} \}$ 

The differences between DFA's and NFA's occur in the definition of $\delta$, namely:

1. $\lambda$ is a valid input for an NFA
2. More than one state may be reached by the same input symbol
3. It is possible that no transitions exist at all for a particular input (an implicit jail)
We can have Automata, that are very similar to [[Deterministic Finite Automata]] but have branches based off the same inputs, it is no longer surjective.


Lambda:
The lambda is a free ride, and if we have $a \lambda$ its equivalent to having $ab$ 

