
[[Theory of Computing]]
A deterministic finite automaton (DFA) is a [[Finite State Machines|finite state machine]] consisting of the following:
- Q, A set of states, one of which is the initial (Or start) state, and a subset of which are final (or accepting) states.
- $\Sigma$, an alphabet of valid input symbols
- $\delta$ which is delta, and it represents a function where it takes Q and $Sigma$ and maps that two another value of Q
$$\delta : Q \times \Sigma \to Q$$
So if $Q$ = $\{s_0, s_1\}$
and $\Sigma$ = $\{a, b\}$
$Q \times \sigma = (S_0, a), (s_0, b), (s_1,a) (s_1,b)$ 

1. The transition function, $\delta$, represents the edges (or transitions) of the machine
2. The subset of Q, comprising the final states, could be empty.