Status: 

Tags: [[Data Structures]]
# List

This is just a version of [[Arrays]], but supporting a couple "nice to have" features like hiding some of the complexity. 

**Resizing** 
To resize when an array gets full we just make a new one and copy over the values from the old array, and because we have to copy all of the elements this takes O(N). This means that we don't want to resize very often, but we also don't want to use too much memory. WE can fix this by using geometric resizing where instead of just using a constant addition we make a new array that is size = old_size * factor 

**Invariants**
- Position of the next element is always the size
- Size is the number of items in the list
- last item is always size -1 

# References
[[Arrays]]