
2025-12-26

Tags: [[Programming]] [[C]]
# Unity Builds
The idea behind a unity build is to just ignore all of the bs that can occur with many header types and instead form a single file that can be compiled. The simplest version would just be to include each file as such. 
```c
#include<src1.c>
#include<src2.c>
#include<src3.c>
```
Unity builds also have advantages such as giving the compiler even more information, allowing for more aggressive optimizations, and they also tend to compile significantly faster.

# References

