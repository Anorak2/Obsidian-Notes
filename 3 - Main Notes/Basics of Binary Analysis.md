
2025-01-22

Tags: [[Reverse Engineering]] [[Computer Science]]
# Basics of Binary Analysis
Why? We do binary analysis since its pretty common for the source code to be unavailable, this can be for a variety of reasons such as the source code simply being lost or because of a malicious adversary the code to their virus isn't public. Knowing how to recover the software allows for us to understand it, and in the case of viruses lets us protect ourselves from that danger.

**Static Analysis**
This is where we look at the code without actually running it. This has a number of pro's including: We don't need to know the programs inputs, we can analyze every part of the code, and we can analyze binary of a certain architecture without having a machine that matches that architecture.

The cons are that it's challenging since this code is state-less and problems like reading data as if it were code.

**Dynamic Analysis**
This is much easier since we can run the binary and then analyze the instructions and the state reached. The main downside is that even after many runs we might not reach all program instructions

**When do we want to?**
The two main reasons why we might reverse engineer something is for security reasons or software development reasons. Security is straight forward, but we may also do it for software dev reasons such as to interoperate with proprietary software, develop competing software, and evaluate the quality and robustness of software when the source isn't available.

# References

