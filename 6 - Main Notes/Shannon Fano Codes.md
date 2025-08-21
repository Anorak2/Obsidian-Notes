
2024-12-27

Status:

Tags: [[Algorithms]] [[Data]]
# Shannon Fano Codes
The problem with Prefix Free codes is that sometimes a code set is good for a dataset and sometimes it isn't. We can fix this by counting the relative frequencies of each character in a text and then splitting them into two groups with the same total amount of frequencies.

We repeat this process of splitting into two equal groups and then recursing down. 

When we finish this process we end up with a Tree with each character as a leaf node, however while Shannon-Fano is good it is actually **not optimal**

# References
[[Prefix Free Codes]]

[[Tree]]

[[Huffman Coding]]