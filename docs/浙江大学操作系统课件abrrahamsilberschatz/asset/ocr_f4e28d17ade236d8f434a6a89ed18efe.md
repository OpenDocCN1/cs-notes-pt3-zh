# III. Consider the organization of a UNIX file as represented by the Inode.

Assume that there are 12 direct block pointers, and a singly, doubly and triply indirect pointer in each Inode. Further, assume that the system block size and the disk sector size are both 8K. Then

+   1. What is the maximum file size supported by this system?
+   
+   2. Assuming no information other that the file Inode is already in main memory, how many disk accesses are required to access the byte in position 13,423,956?