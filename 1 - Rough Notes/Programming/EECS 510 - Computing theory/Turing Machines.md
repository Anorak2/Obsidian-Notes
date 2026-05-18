
[[Theory of Computing]]

The idea of a Turing machine is that we have a tape, that can be infinite, and a head that can read or write at one place along that tape. The notation would be read/write, direction. What's notable about Turing machines is that anything that is computable can be represented by a Turing machine (Church-Turing Thesis).

**DEFINITION**
- A set of states, $Q$, one of which is the initial state, and a non-empty subset of which, $H$, say, contains halt states
- An input alphabet, $\Sigma$, of language symbols
- A tape alphabet, $\Gamma$, which includes $\Sigma$, a special "blank symbol, and other arbitrary symbols as needed
- A transition function $\delta : (Q-H) \times R \to Q \times \Gamma \times \{\leftarrow, \to\}$   

**SUBROUTINES**
This is basically nesting functions inside of each other, and it means that we can string together multiple functions easily.

**LANGUAGES REPRESENTED BY TURING MACHINES**
A programming language that supports the following 3 constructs is equivalent in computing ability to a Turing machine
1. Sequencing - Stored computations performed in a sequence (like statements)
2. Selecting - Based on a boolean expression (like an if statement)
3. Repeating - until some boolean expression changes (looping)
