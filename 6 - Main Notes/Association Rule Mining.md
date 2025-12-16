
2025-12-10

Tags: [[Data Mining]] [[Data]]
# Association Rule Mining
Given a set of transactions, find rules that will predict the occurrence of an item based on the occurrences of other items in the transaction.

## Terms:
---
- Item set
	- A collection of one or more items
	- Example: {Milk, Bread, Diaper}
- k-itemset
	- An item set that contains k items
- Support count ($\sigma$)
	- Frequency of occurrence of an item set
	- E.g. $\sigma$({Milk, Bread,Diaper}) = 2
- Support
	- Fraction of transactions that contain an item set
	- E.g. s({Milk, Bread, Diaper}) = 2/5
- Frequent Item set
	- An item set whose support is greater than or equal to a `minsup` threshold
- Association Rule
	- An implication expression of the form X → Y, where X and Y are item sets
	- Example: {Milk, Diaper} → {Beer}
- Rule Evaluation Metrics
	- Support (s)
		- Fraction of transactions that contain both X and Y
	- Confidence (c)
		- Measures how often items in Y appear in transactions that contain X

**Task**
- Given a set of transactions T, the goal of association rule mining is to find all rules having
	- support ≥ `minsup` threshold
	- confidence ≥ `minconf` threshold
- Brute-force approach:
	- List all possible association rules
	- Compute the support and confidence for each rule
	- Prune rules that fail the `minsup` and `minconf` thresholds -> Computationally prohibitive

**Association Rules:**
1. Frequent Item set Generation
	– Generate all item sets whose support $\geq$ ` minsup`
2. Rule Generation
	– Generate high confidence rules from each frequent item set, where each rule is a binary partitioning of a frequent item set

**Frequent Item Set Strategies:**
- Reduce the number of candidates (M)
	- Complete search: M=2d
	- Use pruning techniques to reduce M
- Reduce the number of transactions (N)
	- Reduce size of N as the size of itemset increases
	- Used by DHP and vertical-based mining algorithms
- Reduce the number of comparisons (NM)
	- Use efficient data structures to store the candidates or transactions
	- No need to match every candidate against every transaction

## Apriori Rule Mining
#### Apriori Principle
If an item set is frequent, then all of its subsets must also be frequent. Apriori principle holds due to the following property of the support measure:
![[Pasted image 20251211003831.png]]
- Support of an item set never exceeds the support of its subsets
- This is known as the anti-monotone property of support

#### Apriori Algorithm 
 $F_k$: frequent k-item sets
$L_k$: candidate k-item sets

Algorithm:
- Let k=1
- Generate $F_1$ = {frequent 1-item sets}
- Repeat until $F_k$ is empty
	- Candidate Generation: Generate $L_k+1$ from $F_k$
	- Candidate Pruning: Prune candidate item sets in $L_k+1$ containing subsets of length k that are infrequent
	- Support Counting: Count the support of each candidate in $L_k+1$ by scanning the DB
	- Candidate Elimination: Eliminate candidates in $L_k+1$ that are infrequent, leaving only those that are frequent => $F_k+1$
	
# References
[[Types of Data Sets|Market Basket Data]]