
2025-02-06

Tags: [[High Performance Computing]] [[Programming]] [[C]]
# Parallel Merge Sort in cilk
Most divide and conquer algorithms have a:
- Divide 
- Conquer 
- Merge

```
mergeSort(A,i,j)
	if i = j
		return
	else
		k = (i+j)/2
		cilk_spawn mergeSort(a,i,k)
		cilk_spawn mergeSort(a,k+1,j)
		cilk_sync
- 
```

**Serial merge Sort**
$M_\infty(n)=\theta(n)$ 
$T_\infty(n)=\theta(n)$ 
$\hat p(n)=\theta(\lg n)$ 

**Parallel merge**
$T_1(n) = \theta(n \lg n)$ 
$T_\infty (n) = T_\infty(n/2) + M_\infty(n)$ 
		$M_\infty(n) = \theta(\lg^2 n)$
$T_\infty(n) = \theta(\lg^3 n)$ 
$\hat p(n) = \theta(\frac{n}{\lg^2n})$ 
# References
[[Merge Sort]]
