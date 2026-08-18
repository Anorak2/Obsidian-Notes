
2025-05-15

Tags: [[Operating Systems]]
# FAT and EXT2 Filesystems
Already covered the basics of FAT in the [[Filesystems and Files]] notes, but some things are still worth mentioning, for example **Clustering**. In this approach the file area is divided into clusters based on the FAT table size, but it can vary from about 4 KB to 32 KB.

#### Linux EXT2 System
EXT2 Disk layout: Disk is divided into several block groups and each block group has a copy of superblock so that you can recover when it is destroyed.

**Super blocks:** These contain basic filesystem information: block size, total number of blocks, total number of free blocks, total number of inodes, etc. Superblocks are needed to mount the filesystem (load it so that blocks can be accessed).


**Journaling:** What happens if the power cut out while using your computer? If the system crashed then all new files that were created are now lost and recovery may not be possible. The idea behind Journaling is that we can keep a log of all changes to the filesystem, and then update the actual filesystem some time later.

**Journaling Procedure**: Begin the transaction, write changes to the log (journal), end transaction (Commit), and at some point checkpoint and synchronize the log with the filesystem. To recover we can check the logs since the last checkpoint and if a log was committed then we can apply it to the filesystem, and if it wasn't committed just ignore it.


# References
[[Filesystems and Files]]

[[Directories]]
