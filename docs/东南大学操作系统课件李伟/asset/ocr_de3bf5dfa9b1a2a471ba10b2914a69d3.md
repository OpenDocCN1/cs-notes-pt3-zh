# Selecting a Disk-Scheduling Algorithm

+   - **SSTF** is common and has a natural appeal
+   - **SCAN and C-SCAN** perform better for systems that place a heavy load on the disk.
+   - Either **SSTF or LOOK** is a reasonable choice for the default algorithm.
+   - Performance depends on the number and types of requests.
+   - Requests for disk service can be influenced by the file-allocation method.