# Linked Allocation

+   - Allocation on basis of individual block
+   - Each file is a linked list of disk blocks: blocks may be scattered anywhere on the disk.
+   - The directory contains a pointer to the first and last blocks of the file.
+   - Each block contains a pointer to the next block in the chain
+   - There is no external fragmentation.
+   - Any free block on the free-space list can be used to satisfy a request.

![](bbox=[0.294, 0.595, 0.596, 0.756])