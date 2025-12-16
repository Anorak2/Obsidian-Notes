Tags: [[Data Structures]]
# Tries

Where as with [[Binary Search Trees|BSTs]] we require that our keys are comparable and with [[Hash Tables]] we require that data is hashable, with Tries we instead require that all of our keys are strings. This enables us to do something pretty cool, we can set each node to only store one letter, and to find if a word is contained in our structure we can traverse these trees. Tries are great for algorithms specific to strings, such as an autocomplete implementation.
![[Pasted image 20241128235554.png]]       ![[Pasted image 20241128235728.png]]
We can also have tries work as maps, where at the end node of a certain word we could store a value such as a number.

**Alternate Idea: Data Indexed Char Map**
This idea is where we have a series of maps that point to other maps, and this idea is very very fast but it requires a very large amount of memory to store all of these maps

**Alternate Idea: Hash-Table Based Trie**
Similar to before, we have hash tables that point to other hash tables. This idea is almost as fast as the the map based one but uses a little bit less memory.

**Alternate Idea: Balanced BST**
This implementation is a little bit slower than the hash table, and it uses a similar amount of idea.

**Performance**
Using a BST or a Hash Table to store links to children will usually use less memory
- DataIndexedCharMap: 128 links per node.  
- BST: C links per node, where C is the number of children. 
- Hash Table: C links per node.  
- Note: Cost per link is higher in BST and Hash Table.

Using a BST or a Hash Table will take slightly more time
- DataIndexedCharMap is Θ(1).  
- BST is O(log R), where R is size of alphabet.  
- Hash Table is O(R), where R is size of alphabet


**Special Algorithms**
This is where the main appeal of Tries in general comes into play, because with our structure it becomes pretty easy to efficiently do certain string operations. One example is prefix matching, where we want to find all strings that start with say "sa" this problem becomes very easy.

A useful application of that prefix algorithm is auto completing words, for example google autocomplete. The problem we reach if we try and do this is that with a very short prefix we generate billions of keys when we only care about say 10. We can address that by having each node store not only its own value but also the value of its best substring, and then we only need to go down branches with high substring scores. An even more efficient thing we can do is called a [[Radix Trie]] where we merge nodes that are redundant.
# References
[[Tree]]

[[Binary Search Trees]]