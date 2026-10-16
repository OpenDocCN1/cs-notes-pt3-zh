# Slab allocation

+   - A **slab** is made up of one or more physically contiguous pages.
+   - A **cache** consists of one or more slabs.
+   - There is a single cache for each unique kernel data structure
+     - Cache for PCBs
+     - Cache for file objects
+     - Cache for semaphores
+   - Each cache is filled with objects -- instantiations of the kernel data structure the cache represents.