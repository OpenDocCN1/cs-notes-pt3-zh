# From Lists to B-Trees

+   - ext4 and NTFS encode directories as B-Trees to improve lookup time to O(log N)
+   - A B-Tree is a type of balanced tree that is optimized for storage on disk
+     - Items are stored in sorted order in blocks
+   - Suppose items *i* and *j* are in the root of the tree
+     - The root must have 3 children, since it has 2 items
+     - The three child groups contain items *a* < *i*, *i* < *a* < *j*, and *a* > *j*