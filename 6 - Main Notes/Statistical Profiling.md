
2025-12-19

Tags: [[Performance Measurement & Reliability]] [[High Performance Computing]]
# Statistical Profiling
## What is it?
First, the downside with instrumentation is both that it can be tedious and that it inherently introduces overhead. Instrumentation can also be frustrating if you are trying to only measure several small portions of the program. One alternative method is statistical profiling, with the idea of at random intervals stopping the execution flow and checking where the current instruction pointer is. Given large enough samples this technique will produce hot-spots since the program will spend longer amounts of time executing there. 

The **Downside** is that due to features such as [[Pipelining]] "now" isn't particularly well defined, so to get a breakdown at an instruction level we need an even more granular technique such as simulation.


**Hardware Events:**
Fortunately for us programmers, there are performance counters built directly into microprocessors capable of storing useful information about programs. These counters are cheap since they are just binary counters with wires, and they can be incremented on hardware events such as a branch mispredict or a cache miss.


## Ex: Perf
Some starter notes, perf is a linux only tool. On debian it can be installed from apt with the name `linux-perf`. Furthermore for the tools necessary to set perf you may need to edit the file present in `/proc/sys/kernel/perf_event_paranoid`. The big idea is that important data could be leaked via a side channel attack for monitored processes, see more [here](https://www.kernel.org/doc/html/latest/admin-guide/perf-security.html). I'll also note that Vtune is available on windows if I ever need it.

**Perf** is a command line application that is very flexible with the programs it can test, and it can even capture OS behavior. One of the simplest ways to use perf is to have it generate a report using `perf stat ./run` to generate a report of the basic events.
![[Pasted image 20251219232108.png]]
`Perf list` will show all of the supported events, and then you can select specific events using `-e`, an example of a nonstandard one is cache-references.


To perform **statistical profiling** we instead want to use `perf record <cmd>` which records the profiling data and dumps it as a `perf.data` file, which can be read with `perf report` to inspect it.

commands:
- `perf stat ./bin` for quick program wide results
	- `perf list` will show specific events you can log using `-e event`
- `perf record ./bin` to generate detailed logs
	- `perf report` to get a detailed breakdown of specific functions with assembly
	- `perf report perf.data` to show individual samples, or to generate a flame graph

# References
- [[Side Channel Attacks]]
- [[Program Instrumentation]]
- [[Program Simulation]]

- [Algorithmica](https://en.algorithmica.org/hpc/profiling/events/)
