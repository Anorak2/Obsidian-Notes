
2025-12-26

Tags: [[Software Engineering]]
# Test Driven Development
Test driven development is a design practice with the goal of producing more reliable software, with the idea that developers might fit their test cases to the code rather than generate representational test cases. TDD solves this by having the programmer write representative test cases that fail, and then developing software that satisfies those test cases. In "pure" TDD you **only** write the minimum amount of code to satisfy the test cases, i.e. if I only had the case add(2, 5) -> 7 then `return 7` would be "correct" under TDD.

**Process:**
1. List scenarios for the new feature
2. Write a test for an item on the list
3. Run all tests. The new test should _fail_ – for _expected_ reasons
4. Write the simplest code that passes the new test
5. All tests should now pass
6. Refactor as needed while ensuring all tests continue to pass
7. repeat
# References

