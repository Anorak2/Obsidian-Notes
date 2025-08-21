
2025-05-02

Tags: [[Security]] [[Operating Systems]] [[Access Controls]]
# File Protection
**Method 1: Access Control List**
Each object stores the users and their permissions, an easy example is how we handle files on linux with things like ls -l. ```-rw-rw-r--``` is an example, it shows the owner, the group, and then the world at the end. So for that file the owner can R/W, the group members can R/W, but world can only read.

**Method 2: Capability List**
This is where each domain tracks which objects can access which files. An example would be like an Access Control Matrix.



# References

