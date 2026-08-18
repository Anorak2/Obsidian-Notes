
2026-07-12

Tags: [[Performance Measurement & Reliability]] [[Designing Data Intensive Applications]]
# What is Reliability

Typically we expect software to:
- do the function the user expects
- tolerate the user making mistakes, or using the software in unexpected ways
- have good enough performance so as not to be limiting 
- prevent unauthorized access and abuse.

Reliability means that we are able to maintain this rough idea of working correctly even when things go wrong, whether internal or external. The things that can go wrong are called **faults**, and systems that anticipate faults and can cope with them are called **fault-tolerant** or resilient. This is like saying something is bullet resistant in the sense that it is impossible to have a system capable of withstanding every possible fault, but there are levels to reliability.

## Hardware Faults
Generally this is less impactful in today's environment than it used to be, but a hardware fault would be a drive failing or a CPU dying. Due to redundant components, and a growing shift to infrastructure as a service this makes total machine failure uncommon and often abstracted away from the programmer.

As parallelism has taken over there has also been a move towards systems that can tolerate the loss of a machine because despite improvements scaling up to many machines in turn scales the number of hardware faults. This also has the added benefit of allowing for rolling upgrades rather than planned downtime.

## Software Errors
This form of fault is particularly nasty since it may not be contained in the same way that hardware faults are, they can be strongly correlated among nodes. For example maybe a system dependency, such as DNS or otherwise, that the system is relying upon goes down. There may be a runaway process, or a memory leak, and these failures can cascade across nodes as well. This is a hard problem to fix, and the best tool available is constant assertion checks against guarantees or assumptions so that when something breaks an alert is raised.

## Human Errors
To design around unreliable humans, which cause the majority of outages, good systems:
- are designed in such a way that it is "hard" to make an error. API's and interfaces should be designed so that it is easy and intuitive to do "the right thing." Part of this is removing complexity and improving clarity where possible. If the system is too restrictive however people **will** try to find hacks or workarounds
- Provide full non-prod sandboxes so that people can experiment without any risk to real data.
- thoroughly test all levels of the system
- Make it easy to recover from errors, such as with rollbacks.
- Set up detailed and clear monitoring for observability
- Training on how to use the system.
# References
- 