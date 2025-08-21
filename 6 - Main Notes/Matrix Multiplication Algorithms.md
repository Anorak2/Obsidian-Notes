
2025-02-06

Tags: [[Math]] [[Programming]] [[Computer Science]] [[High Performance Computing]] [[Algorithms]]
# Matrix Multiplication Algorithms
## Approach 1 - Simple For Loop
```
mm(A,B,C, n)
	cilk_for(i=0;i<n; i++){
		cilk_for(j)
			cilk_for(k)
				C[i][J] += A[i][k] * B[k][j]
	}
```
Drawback is the lack of cache efficiency since we aren't pre-loading B

## Approach 2 - Blocked/Tiled
``` 
mm(A,B,C, n)
	cilk_for(b_i =0;bi <n; i++){
		cilk_for(bj)
			cilk_for(bk)
				Cij += Aik * Bkj
				// This is three more for loops, and we can actually
				// use mm() here
	}
```
This is faster since we are loading multiple numbers for each tile, and this faster read/write is what gives us the faster time. To make sure this works though we have to make the blocks small enough that they fit inside of the cache, say $32 \cdot 32$.


$T_1(n) = \theta(n^3)$ 
$T_\infty(n) = \theta(s^2 n)$ 
$\hat p (n) = \theta(\frac{n}{s}^2)$ 
## Approach 3 - Divide and Conquer
We can split the matrix C, A, and B into four equal segments. This way if it was n across, each block is now n/2 across.

assume n is a power of 2

```
DAC_mm(A, B, C, n)
	if n == 1:
		C = A * B // the base case
	else
		create a new n*n matrix t 
		partition A,B,C,T into n/2 * n/2 matrices
		
		cilk_spawn DAC_mm(A_11, B_11,C_11, n/2)
		cilk_spawn DAC_mm(A_11, B_12,C_12, n/2)
		cilk_spawn DAC_mm(A_21, B_11,C_21, n/2)
		cilk_spawn DAC_mm(A_21, B_12,C_22, n/2)
	
		cilk_spawn DAC_mm(A_12, B_21,T_11, n/2)
		cilk_spawn DAC_mm(A_12, B_22,T_22, n/2)
		cilk_spawn DAC_mm(A_21, B_21,T_21, n/2)
		cilk_spawn DAC_mm(A_21, B_22,T_12, n/2)
		cilk_sync

		add each row in T to each row in C
```

$T_1(n) = \theta(n^3)$ 
$T_\infty(n) = \theta(lg^2n)$ 
$\hat p (n) = \theta(\frac{n^3}{lg^2n})$ 

## Approach 4 - Divide and Conquer 2
Here we can remove the T matrix from the last one to gain space, although it is a little slower

```
DAC_mm(A, B, C, n)
	if n == 1:
		C += A * B // the base case
	else
		partition A,B,C into n/2 * n/2 matrices
		
		cilk_spawn DAC_mm(A_11, B_11,C_11, n/2)
		cilk_spawn DAC_mm(A_11, B_12,C_12, n/2)
		cilk_spawn DAC_mm(A_21, B_11,C_21, n/2)
		cilk_spawn DAC_mm(A_21, B_12,C_22, n/2)
		cilk_sync

		cilk_spawn DAC_mm(A_12, B_21,C_11, n/2)
		cilk_spawn DAC_mm(A_12, B_22,C_22, n/2)
		cilk_spawn DAC_mm(A_21, B_21,C_21, n/2)
		cilk_spawn DAC_mm(A_21, B_22,C_12, n/2)
		cilk_sync
```

$T_1(n) = \theta(n^3)$ 
$T_\infty(n) = \theta(n)$ 
$\hat p (n) = \theta(n^2)$ 

## Approach 5 - Strassen's Algorithm
- So far all of the algorithms take $\geq \theta(n^3)$ 
- Strassen's takes $\theta(n^{2.81})$ 
- We can do this because Strassen's takes only 7 multiplications instead of 8, but we use 14 more additions

**Parallel Implementation**
- 10 Parallel Additions
- 7 Parallel Multiplications
- 8 Additions
# References

[[Matrix Multiplication]]