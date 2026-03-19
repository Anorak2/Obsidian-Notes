
2025-02-03

Tags: [[linux]] [[Reverse Engineering]]
# Linux Linking
Both soft and hard links function like pointers do in programming languages, links in UNIX point to a file or directory. Links function like a shortcut to a file and they allow more than one file name to refer to the same file.

### Hard Links
Each hard linked file is assigned the same Inode value as the original file, which means that they have the same physical place in memory. This allows for a hard linked file to be able to find the other even if the files are moved or even deleted, although changes are still reflected.

You also can't create a hard link to a directory since it works off of Inode data.
### Soft Links
A soft link is just a pointer to a file/directory, and unlike a hard link we don't do any memory trickery. For example if we delete/move a file that is hard linked to another file, the hard link can still access it but a soft link couldn't do that.


# References

