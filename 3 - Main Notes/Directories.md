
2025-04-21

Tags: [[Operating Systems]] [[Operating Systems]]
# Directories
Directories seem different but really as far as the OS is concerned they are just a special type of file that contains the name of the directory and a table of filenames and inode number pairs.

**file structures and file paths**
Directories are traditionally set up in a tree structure, though we can also use symbolic links to point to the same file or hard links to use that same file under a different name. We can navigate directories with paths which give a unique name of a file or directory in a filesystem, but to make something usable we use name resolution which is the process of converting a path into an inode.

To find how many disk accesses we need to resolve ```/usr/bin/top``` we can plot out the process:
1. Read "/" directory inode
2. Read first data block of ```/``` and search ```usr``` for the inode
3. Read the ```usr``` directories inode
4. Read first data block of ```usr``` and search ```bin``` 
5. Read the ```bin``` directories inode
6. Read first block of ```bin``` and search ```top```
7. Read ```top``` file inode

**Caching to Improve speed**
This method is really slow since in the worst case we could be doing thousands of calls to the disk in the worst case, but we can fix that by caching the dentry structures.

dentry: path -> inode number

this speeds up the name resolution process, and when you first list a directory it could be slow but the next time would be a lot faster. We use hashing for some reason that I'm not exactly sure why.  We also keep only frequently used directory names in memory cache using ```LRU```, or Least Recently Used.


# References

[[Filesystems and Files]]