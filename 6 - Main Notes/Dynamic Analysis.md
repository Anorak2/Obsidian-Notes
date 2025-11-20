
2025-11-16

Tags: [[EECS 677 - Software Security Evaluation]] [[Security]] [[Computer Science]]
# Dynamic Analysis and testing
---
At it's core dynamic analysis is just about running the program and seeing what happens, often used to try and understand a program and to identify bugs.

**Benefits:**
- Finding concrete bugs is really useful
- Scalable
- Sound bug finding

**Limitations of Ordinary Testing**
- Property may not be immediately observable from output alone
- The circumstances under which the issue occurs may not be obvious

## Testing and Suites
The fundamental concept is that we create input/output pairs and then check if the program does what it is supposed to do. Ideally we want to capture a variety of behaviors though, and we refer to the collection of test cases as our test suite. Something else we have to be aware of is factoring out **non-determinism**, this means that we have to factor out details like time into the environment: time is an input, random seed is an input, network response is an input.

####  Scope
- Unit testing: Testing at the sub-module level (e.g. function i/o) 
- Integration testing: Testing at the boundary between modules (e.g. library interfaces)
- Application testing: testing at the whole-program level

#### Program Visibility
- Black Box. Testing with “no” information about how the analysis target is architected (typically means binary only)
- White Box. Testing with “complete” information about the analysis target (typically means source code)
- Grey Box. Testing with “some” information about how the analysis target is architected (binary + some static analysis / probing)

#### Classic Problems with testing
It’s hard to predict what might go wrong (presumably you’d have fixed it in this first place). We can try to fix this by trying to make testing more intentional, test driven development, or try to leverage tools like with fuzzing.
# References
[[Fuzzing]]
