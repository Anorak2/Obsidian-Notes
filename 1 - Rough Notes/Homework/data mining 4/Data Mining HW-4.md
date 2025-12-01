## 1
---
![[Pasted image 20251130233228.png]]
	a. Since there are 5 unique items we can generate a maximum of $2^5$ or 32 rules
	b. it's less than or equal to N * W * M, or 10 (rows) *  52 ($\sum$ of items in basket) * 5 (candidates). This works out to 2600
	c. {(A,B,D), (B,D,E), (A,D,E), (A,B,E), (A,C,D), (C,D,E), (A,C,E), (B,C,D), (B,C,E), (A,B,C)}.  I used "manual brute force" resulting in 10 possible combinations
	d. {D,E} has support 6
	e.  {C, E} has a relation such that {C} -> {E} and {E} -> {C} have the same support
## 2
---
![[Pasted image 20251201010200.png]]

## 3
---
![[Pasted image 20251130234740.png]]
	a. Data set 2 will produce more item sets since it has fewer transactions that will be pruned
	b. 4, since one data set will be pruned for some of its transactions being very rare
	c. Data set 1 since it has the widest single box
	d.Data set 1 
	e. Data set 2

## 4
---
	a. (4, 2.5), and maybe (1, 4.5)
![[Pasted image 20251201000121.png]]
	b. Based on the given numbers the following are outliers:  {(4.00, 2.50), (3.31, 3.73), (0.94, 4.48), (4.17, 5.85), (4.63, 3.92)}
![[Pasted image 20251201000219.png]]
	c.  Based on the given numbers the following are outliers: 2.5 {(4.00, 2.50), (3.31, 3.73), (0.94, 4.48)}
![[Pasted image 20251201000238.png]]
	d. I would say that based on this limited example LOF performed significantly better, it identified the same two outliers I identified visually and didn't hit the same number of "bystanders" that 10th nearest neighbor did. 10th nearest also didn't identify (0.94, 4.48) which I would classify as a failure