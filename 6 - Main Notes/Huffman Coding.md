
2024-12-27

Status:

Tags: [[Algorithms]] [[Data]] [[Data Structures]]
# Huffman Coding

**Algorithm:**
Calculate the relative character frequencies
- Assign each symbol to a node with weight = relative frequency
- Take the two smallest nodes and merge them into a super node with weight equal to sum of weights
- Repeat until everything is part of a tree

For simplicity we can just make every right connection a 1, and every left connection a 0. What is interesting is that this approach is **Strictly** better than [[Shannon Fano Codes]], and there is literally no downside to using Huffman Coding. Actually pretty neat since usually there is some kind of trade off.

**Implementing Encoding**
There are two schools of thought when implementing with a data structure:
- [[Arrays|Array]] Based, using each characters number as an index
- [[Hash Tables|Hash map based]], since we are just doing a Hashmap<Character, BitSequence>

Compared to HashMaps, the array based version is just faster but they use more memory if some characters of the alphabet are unused. 

**Implementing Decoding**
For decoding, which is turning a compressed bit stream back to a bit stream we need to look up the longest matching prefix, which [[Tries]] are perfect for.

**In Practice**
In practice there are two philosophies for using Huffman compression
1. For each input type (Images, English, Chinese, ...) get a huge number of sample inputs for that category to create a standard code for each of those
2.  For every input file, create a unique code just for that file and send the code along with the compressed file

The first one has problems like what if the file has multiple data types, although it could be faster since the code is already built in. For the second one the individual code is more "secure" but also requires more work for compressing each file. If the data is not compressible then you may as well use approach 1, but both allow for supporting arbitrary file types.

1. Approach 1 results in sub-optimal encoding
2. Approach 2 requires extra space for the code-word table, but for very large inputs this is insignificant. In practice this is the approach we use


# References
[[Prefix Free Codes]]

[[Shannon Fano Codes]]

[[Tree]]
