# Batching

+   - Frequently it is possible to group requests for more efficiency
+     - Amortize overheads of processing
+     - Schedule requests for better performance
+   - Examples: N messages vs. one message with N requests Disks:
+     - Always transfer a bunch of bytes (sector or block)
+     - Schedule the disk motions