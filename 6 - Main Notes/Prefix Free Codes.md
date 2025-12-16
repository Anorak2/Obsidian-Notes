Tags: [[Algorithms]] [[Data]]
# Prefix Free Codes

The idea behind Prefix free codes is that it sucks to store symbols, for example letters, as a full 8 bit number. So what if instead we just used fewer bits. An example of this is Morse code but the problem we run into is that sometimes our codes are ambiguous.

**Solution:**
If we look at Morse code represented in a [[Binary Search Trees]] with . being left and dash being right we can see that E has children which is what causes the confusion. However, if we instead make it so that every symbol we can use is a leaf then there cannot be any confusion, since when we hit a leaf we are done searching for our letter. 

Something that is interesting is that some prefix-free codes are better than others for certain strings. It would actually be really helpful if we could find some kind of algorithm to generate the "optimal" code for a given text.

![[Pasted image 20241210225758.png]]

# References
[[Tree]]