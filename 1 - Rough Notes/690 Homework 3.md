[[High Performance Computing]]

We start by finding the total number of brick sorts we are doing. There are $\ln n +1$ steps for shear sort where for each step we need to do exchanges:
$$\text{total compare splits}=(\ln n+1) \cdot brick_{count}(row/col)$$
Now we just need to find the total number of operations for the second brick sort implementation. 

The way I solve this is we already have a 2d pattern showing the steps and when we add a new processor that means both a new row and a new column. Both of these have a length of p, so we are adding $2p-1$ boxes since we can't double count the bottom right one. Every box we add to the sorting network has to do a compare split operation every other time, which would equal:
$$brick_{count}(1)=0$$
$$brick_{count}(p)=floor(\frac{2(p-1)}{2})+brick(p-1)$$

which simplifies to:

$$brick_{count}(1)=0$$
$$brick_{count}(p) = p-1 +brick(p-1)$$

as a sum this is $(p-1) + (p-2) + (p-3)... + 2 + 1$ which is equivalent to 
$$\frac{(p-1)p}{2}$$
which then substituted back into the original function we get:
$$(ceil(\ln n) + 1)\frac{(p-1)p}{2}$$
but since n is always a power of 2 we can simplify to 
$$(\ln n + 1)\frac{(p-1)p}{2}$$
