# Multilevel Index

![](bbox=[0.0, 0.02, 0.08, 0.15])

+   - If primary index does not fit in memory, access becomes expensive.

+   - Solution: treat primary index kept on disk as a sequential file and construct a sparse index on it.
+     - outer index – a sparse index of primary index
+     - inner index – the primary index file

+   - If even outer index is too large to fit in main memory, yet another level of index can be created, and so on.

+   - Indices at all levels must be updated on insertion or deletion from the file.