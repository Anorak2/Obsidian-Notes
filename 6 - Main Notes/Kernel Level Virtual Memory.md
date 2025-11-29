
2025-04-09

Tags: [[Operating Systems]] [[Operating Systems]]
# Kernel Level Virtual Memory
This is the idea that we have a section of memory where we can store the kernel code and data. This section is identical to all address spaces and has a fixed 1-1 mapping of physical memory. We then also have a larger section for user memory where we can have the process code, heap, data, stack... that is unique to each address space and is on demand. Using this approach means the kernel always has some memory allocated to it, preventing deadlocks as well as having memory isolation for security purposes.

# References
[[Virtual Memory and Paging]]

[[Virtual Memory 2]]
