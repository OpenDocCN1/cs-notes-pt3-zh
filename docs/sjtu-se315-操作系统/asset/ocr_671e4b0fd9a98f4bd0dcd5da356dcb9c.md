# Implementing Extents

+   - ext4 and NTFS use extents
+   - ext4 inodes include 4 extents instead of block pointers
+     - Each extent can address at most 128MB of contiguous space (assuming 4KB blocks)
+     - If more extents are needed, a data block is allocated
+     - Similar to a block of indirect pointers