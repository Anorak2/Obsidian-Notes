
2025-11-16

Tags: [[EECS 677 - Software Security Evaluation]] [[Dynamic Analysis]]
# Program Instrumentation
The basic idea here is to write code into the executable to gather information.  This addresses the two major issues with basic testing, property may not be observable on output alone and non-obvious circumstances. Program Instrumentation can report upon program state and even program path.

**Inserting Probes**
Insert checks / reports into the analysis target addresses both of the previous issues – can report upon program state and even program path. Adds a new concern though, the efficiency of the (instrumented) program since it adds a **potential slowdown** on each program path. Old concern -- the efficiency of placement analysis somewhat **limited** by the information the probes can report.

**Example:**
We can count the number of times certain program behaviors are exercised. The ones you, Adam, are most familiar with are [[Tracing|strace and ltrace]]. Yeah I know who you are :D.


#### Two Forms
Program Instrumentation can really fall into two forms:
- [[Static Instrumentation]] -- Alters the program statically to gain information at runtime
- [[Dynamic Instrumentation]] -- Alter the program at runtime, potentially leveraging runtime info
# References
[[Tracing]]

[[Static Instrumentation]]

[[Dynamic Instrumentation]]
