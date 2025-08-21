
2025-02-17

Tags: [[Algorithms]][[Computer Science]]
# Peterson's Race Condition Solution
This is a purely software fix the the problem of race conditions, and the code only needs to share two variables: one for whose turn it is to access the critical section, and one as a flag to show that the code wants to access a critical section.

Before we access the critical section, we check and wait if it is the other threads turn and if it has reached the critical section

![[Pasted image 20250217143005.png]]

Something to keep in mind is that we can't re-order any of these instructions since otherwise it would break.
# References
[[Race Conditions]]