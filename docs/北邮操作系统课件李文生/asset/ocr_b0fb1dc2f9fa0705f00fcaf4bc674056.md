# Fragmentation

+   - **External Fragmentation** – total memory space exists to satisfy a request, but it is not contiguous.
+   - **Internal Fragmentation** – allocated memory may be slightly larger than requested memory; this **size difference** is memory internal to a partition, but not being used.
+   - **Reduce external fragmentation by compaction**
+     - Shuffle memory contents to place all free memory together in one large block.
+     - Compaction is possible only if relocation is dynamic, and is done at execution time.
+     - **I/O problem**
+       - Latch job in memory while it is involved in I/O.
+       - Do I/O only into OS buffers.