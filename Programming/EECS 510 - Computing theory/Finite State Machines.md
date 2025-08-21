
[[Theory of Computing]]

We can create machines using [[Grammars]]

$$E \to \lambda \mid aO \mid bO$$
$$O \to aE \mid bE$$

We need two states, E and O with E being our start state and end states.

we can get between states by adding a/b

| State | Remaining Input |
| ----- | --------------- |
| E     | abba            |
| O     | bba             |
| E     | ba              |
| O     | a               |
| E     | $\lambda$       |
 Can we build a machine that accepts all and only those strings over the alphabet $\Sigma = \{0, 1\}$ that end with the symbol 1.  
