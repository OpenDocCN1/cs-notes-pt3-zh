# Slab allocation

+   - **When cache created, filled with objects marked as free**
+     - The number of objects in the cache depends on the size of the associated slab.
+   - **When structures stored, objects marked as used**
+   - **If slab is full of used objects, next object allocated from empty slab**
+     - If no empty slabs, new slab allocated
+   - **Benefits**
+     - no fragmentation
+     - fast memory request satisfaction