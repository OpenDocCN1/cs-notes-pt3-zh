# What Does fsck do?

+   - 6. Check bad blocks
+     - E.g., point to some out-of-range address
+     - What should fsck do? Just remove the pointer
+   - 7. Check directories
+     - The only file that fsck know more semantic
+     - Making sure that “.” and “..” are the first entries
+     - Ensure no dir is linked more than once
+     - No same filename in one dir