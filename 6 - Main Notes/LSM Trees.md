
2026-07-16

Tags: [[Designing Data Intensive Applications]] [[Data]] [[Algorithms]] [[Data Structures]]
# LSM Trees
LSM Trees are typically used in databases that prioritize high write throughput, and we can accomplish this by using a series of append only files so that we are never performing a random write. This model keeps layers in different layers of accessibility, from locations held in an in-map memory to values held some segments further. This model is used in several different databases such as `LevelDB` and `RocksDB`, and Cassandra and `HBase` are both similar to this idea. 


**Storage Engine Workflow:**
- When a write comes in add it to a balanced tree structure, or memtable, such as a Red-Black Tree.
- In order to prevent recent writes from being lost append the write to a write ahead log*
- When the memtable gets bigger than some threshold, often a few megabytes, write it out to disk as an SSTable file. This can be done efficiently because the tree already maintains the key-value pairs sorted by key. The new SSTable file becomes the most recent segment of the database. When the new SSTable is ready, the memtable can be emptied.
- In order to serve a read request, first try to find the key in the memtable, then start checking the segments starting at the most recent.
- From time to time, run a merging and compaction process in the background to combine segment files and to discard overwritten or deleted values.

\* The log isn't sorted like the SSTable but it doesn't matter since this log exists only for recovery, likewise during the compaction stage this file can be deleted since it is no longer needed.


## Components + Explanation
**Hash Indexes**
This is a key/value storage system, and like hashmaps they provide both fast reads and fast writes. The simplest way to use a hash index would be to have each key mapped to a byte index in a file, and this approach is actually valid. One tricky part is that modifying any data in the file means invalidating every address. We solve this by making the file append only, and the map points only to the most recent change.

Since this solution wastes space instead what happens in these systems is that we break out our log files when they reach a certain size, and then perform compaction. By compacting the data we throw out duplicate instances of the keys and only keep the most recent update. If these segments are compacted enough we can also further merge the newest segment with another segment.

Segments are append only files, so the merged segment is written to a new file. The merging and compaction can be done in the background on a separate thread, enabling continuous operation using the old segment files. After the merging process is finished, read requests are switched to the new merged segment instead of the old segments.  Old segment files can simply be discarded.

**SSTables**
Sorted String tables are like this previous log storage segment, but on top of the previous one key requirement we also require that the files are sorted by the **key** of the key value pair. This fixes several problems, and improves the overall efficiency. First this approach is easy to implement using an algorithm similar to merge sort. Second, keys no longer need to be kept in an in-memory index, they can be stored at the top of the file. Since the keys are sorted it is easy to perform a binary search on the location, and only one key is needed per every few kilobytes since kilobytes are easy to scan. Since this system requires reading several kilobytes worth of data, it is also more efficient to compress blocks given that data is the bottleneck rather than CPU cycles.
![[Pasted image 20260717003948.png]]
The easiest way to maintain a sorted structure is to do so in-memory with a Red-Black tree or an AVL tree

# References
- [[Hash Tables - Hashmaps]]
- [[Merge Sort*]]
- [[Red Black Trees (LLRB)]]
- [[AVL Trees]