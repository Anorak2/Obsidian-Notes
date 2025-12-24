
2025-12-20

Tags: [[Performance Measurement & Reliability]] [[High Performance Computing]]
# Program Simulation
In previous approaches we gathered the information from various sources, in this approach we instead just simulate the program so that we can have complete information about the program.

## Ex: Cachegrind
```bash
valgrind --tool=cachegrind --branch-sim=yes ./run
```
![[Pasted image 20251220015420.png]]
In this version it only models with the L1 cache and the combined cache.
- I stands for instruction cache
- D stands for data cache
- LL stands for an aggregate, so LLd is all data caches and LL is aggregate details.
# References

