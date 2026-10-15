# Optimization of Disk Block Access(Cont.)

+   - Log disk – a disk devoted to writing a sequential log of block updates
+     - Used exactly like nonvolatile RAM
+       - Write to log disk is very fast since no seeks are required
+       - No need for special hardware (NV-RAM)
+   - File systems typically reorder writes to disk to improve performance
+     - Journaling file systems write data in safe order to NV-RAM or log disk
+     - Reordering without journaling: risk of corruption of file system data