
2025-05-14

Tags: [[Operating Systems]] [[Operating Systems]]
# Filesystems
A filesystem is an OS layer that provides file and directory abstractions on disks. From a users view a file is a collection of non-volatile bytes, but for the OS view a file is a collection of blocks.

**What should the system do?**
The system should not waste space, and it should be fast. It is also worth noting that most files are small and if the block size is too big then it wastes space, however large files will use most of the space and if the block size is too small there will be heavy mapping information.

**File Disk Allocation**
How do we map disk blocks to files? Each file may have very different size, and the size of a file may change over time (grow or shrink) making this rather hard. There are a number of disk allocation methods.

#### Continuous Allocation
This approach uses continuous ranges of blocks. Users declare the size of a file in advance similar to malloc, and each file has a header containing the first block number, and the number of blocks allocated.
- Fast sequential Access
- Easy random access
- Has external fragmentation
- Difficult to increase

#### Linked-List Allocation
In this approach each block holds a pointer to the next block in the file. 
- The pro is that this approach can grow very easily and has no external fragmentation
- The trade off is that the access performance is bad.

**File Allocation Table (FAT)**
A variation of linked allocation where links are not stored in data blocks but in a separate table. There is a fat array with the # of blocks as the number of indexes. 

#### Index Allocation
Use a one per-file index block which holds block pointers for every chunk composing of the file. The directory entry points to a index block and the index block points to all blocks used by the file. 
- Pro: This method has no external fragmentation and fast random access
- Con: There is a space overhead, and there is a file size limit
Since each block has a fixed size we can calculate the maximum file size easily, it is: (size of a block)/(pointer size) * (size of a block)

#### Multilevel Index Allocation
This method is a lot like index allocation, and for small files we can still use direct mapping. However when we have a large file we can have multiple different index files, such as a two or a three level system.
- Pros: Easy to expand, and small files are very fast
- Cons: Large files become costly, and there is still a size limit


**Filesystem caches**
- Buffer cache, which caches disk blocks which are frequently accessed
- Page cache, this deals with memory mapped files

**Virtual File System (VFS)**
This provides the same filesystem interface for different types of file systems which allows for us to abstract them, and it makes it easy to swap to a different one or load a drive with a different implementation. To do this it has a defined API that all used file systems support.

# References
[[Directories]]

[[Singly Linked List]]