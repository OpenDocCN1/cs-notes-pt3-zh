# # Copy-on-Write

+   - Process Creation
+   - Copy-on-Write (COW) allows both parent and child processes to **initially share** the same pages in memory.
+   - If either process modifies a shared page, then only the page is copied.
+   - COW allows more efficient process creation as only modified pages are copied.
+   - Free pages are allocated from **a pool of zeroed-filled pages**.