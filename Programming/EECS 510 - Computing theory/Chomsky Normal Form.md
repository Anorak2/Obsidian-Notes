
[[Theory of Computing]]

The Chomsky normal form is actually pretty similar to the [[Normalization|Database Normal Forms]] and it makes it much easier to formally prove theorems, as well as allows for a couple of algorithms. 

A [[Context Free Grammar]] is in Chomsky Normal Form if all of the production rules satisfy one of the conditions:
- A non-terminal term generating a terminal (X -> a)
- A non-terminal generating two non-terminals (X -> YZ)
- Start symbol generating $\lambda$, (S -> $\lambda$)

**Converting a [[Context Free Grammar|CFG]] to CNF**
1. Eliminate start symbol from RHS (if S is on the RHS such as S -> aS)
2. Eliminate lambda without changing the language generated, and remove all unit productions such as $X \to Y$
3. Eliminate terminals from the RHS if they exist with other terminals or non-terminals, ($X \to xY$ turns to $X \to ZY, Z \to x$ )
4. Eliminate RHS with more than two non-terminals ($X \to XYZ$ can be $X\to PZ$ and $P \to XY$ )
