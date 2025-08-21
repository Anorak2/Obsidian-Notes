Status:

Tags: [[Algorithms]] [[Sorting]]
# Formal Sorting Definition

an ordering relation < for keys a, b, c has the following properties:
- Law of Trichotomy: Exactly one of a < b, a = b, b < a is true.  
- Law of Transitivity: If a < b, and b < c, then a < c.

An ordering relation with the properties above is also known as a “total order”.  

A sort is a [[Permutation]] (re-arrangement) of a sequence of elements that puts the keys into non-decreasing order relative to a given ordering relation.  
-  $x_1 ≤ x_2 ≤ x_3≤ ...≤ x_n$ 

**Stability**
A sort is said to be stable if the order of equivalent items is preserved, 
which sometimes matters for algorithms like [[Radix Sort]]

**Comparison Based Sorts**
Sorting algorithms that are based on comparisons such as [[Merge Sort]] and [[Quick Sort]]. What is interesting is that for **any comparison based sorting algorithm, it requires at least an order of N log N for its worst case**

**Alternative definition**
We can define an inversion as a pair of elements that are out of order with respect to <, and sorting as a sequence of operations that reduces inversions to 0.

# References

[[Best Sorting Algorithm]]