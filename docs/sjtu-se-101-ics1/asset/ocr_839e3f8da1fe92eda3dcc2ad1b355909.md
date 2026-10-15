# Simple segregated storage

+   - Separate heap and free list for each size class
+   - No splitting
+   - To allocate a block of size n:
+     - if free list for size n is not empty,
+       - allocate first block on list (note, list can be implicit or explicit)
+     - if free list is empty,
+       - get a new page
+       - create new free list from all blocks in page
+       - allocate first block on list
+     - constant time