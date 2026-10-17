# # Caches

+   - **Cache**: A smaller, faster storage device that acts as a staging area for a subset of the data in a larger, slower device.

+   - **Fundamental idea of a memory hierarchy:**
+     - For each k, the faster, smaller device at level k serves as a cache for the larger, slower device at level k+1.

+   - **Why do memory hierarchies work?**
+     - Because of locality, programs tend to access the data at level k more often than they access the data at level k+1.
+     - Thus, the storage at level k+1 can be slower, and thus larger and cheaper per bit.

+   - **Big Idea**: The memory hierarchy creates a large pool of storage that costs as much as the cheap storage near the bottom, but that serves data to programs at the rate of the fast storage near the top.