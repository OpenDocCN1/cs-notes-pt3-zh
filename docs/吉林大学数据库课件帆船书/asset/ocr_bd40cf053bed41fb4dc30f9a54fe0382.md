# Choice of RAID Level

+   - Factors in choosing RAID level
+     - Monetary cost
+     - Performance: Number of I/O operations per second, and bandwidth during normal operation
+     - Performance during failure
+     - Performance during rebuild of failed disk
+       - Including time taken to rebuild failed disk

+   - RAID 0 is used only when data safety is not important
+     - E.g. data can be recovered quickly from other sources

+   - Level 2 and 4 never used since they are subsumed by 3 and 5

+   - Level 3 is not used anymore since bit-striping forces single block reads to access all disks, wasting disk arm movement, which block striping (level 5) avoids

+   - Level 6 is rarely used since levels 1 and 5 offer adequate safety for most applications