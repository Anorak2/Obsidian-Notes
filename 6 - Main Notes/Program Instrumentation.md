
2025-11-16

Tags: [[Software Security Evaluation]] [[Dynamic Analysis]]
# Program Instrumentation
The basic idea here is to write code into the executable to gather information.  This addresses the two major issues with basic testing, property may not be observable on output alone and non-obvious circumstances. Program Instrumentation can also share other relevant **state** or **events** such as the average length of input for a hash function, or the size/height of a binary tree. While it is very powerful instrumentation can be tedious.

Program Instrumentation can really fall into two forms:
- [[Static Instrumentation]] -- Alters the program statically to gain information at runtime
- [[Dynamic Instrumentation]] -- Alter the program at runtime, potentially leveraging runtime info
## Inserting Probes
Insert checks / reports into the analysis target addresses both of the previous issues – can report upon program state and even program path. Adds a new concern though, the efficiency of the (instrumented) program since it adds a **potential slowdown** on each program path. Old concern -- the efficiency of placement analysis somewhat **limited** by the information the probes can report.

**Example:**
We can count the number of times certain program behaviors are exercised. The ones you, Adam, are most familiar with are [[Tracing|strace and ltrace]]. Yeah I know who you are :D.

Another way would just be the traditional clock based approach
```cpp
clock_t start = clock();
do_something();
float seconds = float(clock() - start) / CLOCKS_PER_SEC;
printf("do_something() took %.4f", seconds);
```
This approach struggles with very short functions, as I've had issues with in the past. One way to fix this is to generate an average of how long the clock() function takes to run and then deduct it from the end runtime.

#### Versatility and Sampling
As mentioned earlier we may be interested in other parts of our program than simple runtime, such as input length. One downside to adding these to our program is that we introduce extra overhead, which may be relevant. This is actually easy to fix though by instead only updating our counters on a random sample of function calls
```c++
void query() {
    if (rand() % 100 == 0) {
        // update statistics
    }
    // main logic
}
```
As algorithmica mentions what we are actually doing is a [[Bernoulli]] Distribution until we get a success, which is also called a [[Geometric]] distribution. So instead we could use a geometric distribution with a counter.
```c++
void query() {
    static next_sample = geometric_distribution(sample_rate);
    next_sample--;
    if (next_sample == 0) {
        next_sample = geometric_distribution(sample_rate);
        // ...
    }
    // ...
}
```
This allows us to only take a random sample on a success rather than every iteration. Techniques like this can be used in libraries or large products that need this information without slowing down the end product too much.
# References
-  [[Tracing]]
-  [[Static Instrumentation]]
-  [[Dynamic Instrumentation]]
-  [[Statistical Profiling]]

-  [Algorithmica](https://en.algorithmica.org/hpc/profiling/instrumentation/)