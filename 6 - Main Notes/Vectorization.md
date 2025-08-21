
2024-12-27

Status:

Tags:[[Programming]] [[3 - Tags/Optimization|Optimization]] [[Compilers]]
# Vectorization

The idea behind this is that most modern CPU's have either vector or SIMD instruction sets that allow for the same operation to occur simultaneously on multiple pieces of data, such as two four or eight. This will often be done by the compiler without you even realizing it, and it involves unrolling a loop into something like:

```
for (int i=0; i<16; i+=4) {
    C[i]   = A[i]   + B[i];
    C[i+1] = A[i+1] + B[i+1];
    C[i+2] = A[i+2] + B[i+2];
    C[i+3] = A[i+3] + B[i+3];
}
```

where the CPU is then able to do these operations the fast way.
# References
[[Arrays]]

