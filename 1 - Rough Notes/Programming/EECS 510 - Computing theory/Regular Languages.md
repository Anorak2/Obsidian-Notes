
[[Theory of Computing]]

A regular language is a language that can be accepted by a [[Finite State Machines|Finite State Machine]]

Formal Definition:
1. The empty language $\varnothing$ is a regular language
2. for each $a \in \Sigma$ the singleton language $\{a\}$ is a regular language
3. if A is a regular language then $A^*$ is a regular language, this also means that $\{\lambda\}$ is a regular language
4. If A and B are regular languages, then $A \cup B$ and $A \cap B$ are regular languages
5. no other languages are regular

Rule of thumb:
If a language requires memory we cannot model it with a [[Finite State Machines|FSM]] since the memory of state machines is very limited, that means any languages such as $a^n b^n$ aren't regular since we can't store a count