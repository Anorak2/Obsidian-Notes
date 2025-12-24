
2025-12-19

Tags: [[High Performance Computing]] [[Performance Measurement & Reliability]]
# Profilers
When you run into performance issues in a program, the easiest way to diagnose these issues is often with a profiler. While these are great general tools, they still operate on various levels of granularity and their results must be interpreted correctly.

Three main levels of precision:
- **Instrumentation allows** you to treat a program as either a whole or as parts, and count which events you are interested in
- **Statistical profiling** lets you go down to the assembly level and track various hardware events such as branch mispredictions or cache misses. Usually this approach is the perfect mix of flexibility and power.
- **Program Simulation** lets you go down to the individual cycle level and look into what is happening inside the CPU on each cycle when it is executing a small assembly snippet
Others:
- Event-based profilers, for example the jvm tools interface provides hooks for profilers based on events such as calls, class load, etc

# References
[[Static analysis]]

[[Program Instrumentation]]

