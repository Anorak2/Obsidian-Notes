
2026-03-04

Tags: [[Data Mining and Machine Learning]]
# Sequential Search Feature Selection
A greedy algorithm is a problem-solving approach that makes the locally optimal choice at each step, aiming to find a global optimum. By only selecting for the immediate option they often fail to be optimal in the long run but they are fast.
## Sequential Forward Search
Forward search - add the best feature at each step
1. Set of features F initially Ø.
2. At each iteration, find the best new feature x not already in F
3. Add x to F
4. Stop when adding a feature does not improve Accuracy

Maximum iterations = $d$
Maximum k-fold cross-validations = $d(d+1)/2$
## Sequential Backward Selection (SBS)
Backward search – delete the worst feature at each step
1. Set of features F initially includes all features.
2. At each iteration, find the worst feature $x_j$
3. Delete $x_j$ to F
4. Stop when deleting a feature does not improve Accuracy

Maximum iterations = $d-1$
Maximum k-fold cross-validations =$[d(d+1)/2]-1$

## Plus-L Minus-R Selection (LRS)
Generalization of SFS and SBS. LRS attempts to compensate for the weaknesses of SFS and SBS with some backtracking capabilities. Its main limitation is the lack of a theory to help predict the optimal values of L and R.
- If L>R, LRS starts from the empty set and repeatedly adds L features and removes R features
- If L<R, LRS starts from the full set and repeatedly removes R features followed by L additions
```
If L>R then
	F=∅
	Repeat L times
		Find the best feature and add it to F
	Repeat R times
		Find the worst feature and delete it from F
Else
	F=X
	Repeat R times
		Find the worst feature and delete it from F
	Repeat L times
		Find the best feature and add it to F
Endif
```
## Bidirectional Search (BDS)
BDS is a parallel implementation of SFS and SBS, SFS is performed from the empty set and SBS is performed from the full set. To guarantee that SFS and SBS converge to the same solution: Features already selected by SFS are not removed by SBS,  features already removed by SBS are not selected by SFS.
$$
\begin{cases}
1. \text{ Start SFS with } Y_F = \emptyset \\
2. \text{ Start SBS with } Y_B = X \\
3. \text{ SFS: Find the best feature not already removed by SBS and add it to } Y_F \\
4. \text{ SBS: Find the worst feature not already added by SFS and remove it from } Y_B \\
5. \text{  Go to 3} \\
\end{cases}
$$

## Sequential Floating Forward Selection (SFFS)
An extension to LRS with flexible backtracking capabilities. Rather than fixing the values of L and R, these floating methods allow those values to be determined from the data. The dimensionality of the subset during the search can be thought to be “floating” up and down. Notice that in the formula it will loop infinitely unless interrupted.

1. Y = ∅
2. Find the best feature (x) & add it to Y
	1. Y = Y + x
3. Find the worst feature (x)*
4. If the Accuracy of Y – x is better than the Accuracy of Y
	1. Y = Y – x
	2. Go to Step 3
5. Else go to Step 2
## Sequential Floating Backward Selection (SFBS)
1. Y = X
2. Find the worst feature (x) & remove it from Y
	1. Y=Y-x
3. Find the best feature (x)*
4. If the Accuracy of Y + x is better than the Accuracy of Y
	1. Y=Y+x
	2. Go to Step 3
5. Else go to Step 2

\*Notice that you’ll need to do book-keeping to avoid infinite loops
# References
- [[Dimensionality Reduction]] 
