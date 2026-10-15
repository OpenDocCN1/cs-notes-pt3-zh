# L1 cache access

![](bbox=[0.11, 0.23, 0.58, 0.88])

+   - Partition physical address into CO, CI, and CT.
+   - Use CT to determine if line containing word at address PA is cached in set CI.
+   - If no: check L2.
+   - If yes: extract word at byte offset CO and return to processor.