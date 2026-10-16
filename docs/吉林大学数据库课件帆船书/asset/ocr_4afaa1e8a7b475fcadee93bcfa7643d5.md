# Deficiencies of Static Hashing

+   - In static hashing, function *h* maps search-key values to a fixed set of *B* of bucket addresses. Databases grow or shrink with time.
+     - If initial number of buckets is too small, and file grows, performance will degrade due to too much overflows.
+     - If space is allocated for anticipated growth, a significant amount of space will be wasted initially (and buckets will be underfull).
+     - If database shrinks, again space will be wasted.
+   - One solution: periodic re-organization of the file with a new hash function
+     - Expensive, disrupts normal operations
+   - Better solution: allow the number of buckets to be modified dynamically.