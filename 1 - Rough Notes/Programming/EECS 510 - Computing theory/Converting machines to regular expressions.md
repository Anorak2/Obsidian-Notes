
[[Theory of Computing]]

This is the sister theory to [[Converting REGEX to state machines]], except now we must start with a finite automaton and obtain a [[Regular Expressions|regular expression]] that accepts the same language.

Our machine must have the following properties:
1. There are no edges entering the initial state from any other state (self loops are ok)
2. There are no edges leaving any final state to any other state (self loops are ok)
3. There is only one final state and it is not the initial state
4. There is no jail state (simply remove if needed as it does not contribute to the language)