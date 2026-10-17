# # Dynamic Partitioning Placement Algorithm (Cont.2)

+   - **Next-fit**
+     - starts scanning memory from the location of the last placement and chooses the next available block that is large enough
+     - more often allocate a block of memory at the end of memory where the largest block is found
+     - the largest block of memory is broken up into smaller blocks
+     - compaction is required to obtain a large block at the end of memory