
[[Theory of Computing]]

The most intuitive way would be to just use a graph and draw it out.

We could also define:
$Q$, the set of states $Q=\{q_0,q_1\}$
$\Sigma$, the alphabet: $\Sigma = \{a,b\}$
$\delta = \{((q_0,a),q_0),((q_0,b),q_1), ((q_1,a), q_0), ((q_1, b),q_1)\}$



OR a transition table 

| State  | A     | B     |
| ------ | ----- | ----- |
| $q_0$  | $a_0$ | $q_1$ |
| $+q_1$ | $q_0$ | $q_0$ |
Where the + represents acceptance


Regular language - A formal language for which there exists a [[Deterministic Finite Automata]] that accepts all and only those strings in the language