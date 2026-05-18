
[[Theory of Computing]]
How can we prove that there exists and automaton for every regular expression?
Remember our definition from earlier when we had part 1 and 2

a) $\phi$ represents the empty language/set {}
b) $\lambda$, representing the one-string language/set {$\lambda$}
c) c, for each character c in the alphabet $\Sigma$, represents the language/set {c}


**Concatenation**
How could we show the concatenation of two [[Non-Deterministic Finite Automata|NFAs]]?

Imagine if we have two NFAs, NFA 1 and NFA 2. NFA 1 has two accepting states, NFA $1_x$ and NFA $1_y$. We can solve this by putting in NFA 1 x/y in parallel, and then connecting those machines to NFA 2 by just using $\lambda$ 

**Kleene Star**
1. If the empty string is not already accepted, we must add it
2. We must allow arbitrary "restarts" of the NFA

Condition 1 has nuances though,
- if the state of the NFA is also an accepting state, we are already done because it accepts the empty string
- if it is not an accepting state and
	- there are no incoming edges from other states, then we convert it to be accepting
	- There are incoming edges from other states, we must create a new accepting state followed by a lambda transition to the original initial state so that we don't change the behavior of the language

**Union** 
We can show the union of two NFAs by just adding a new initial start state with lambda transitions to the start state of each NFA