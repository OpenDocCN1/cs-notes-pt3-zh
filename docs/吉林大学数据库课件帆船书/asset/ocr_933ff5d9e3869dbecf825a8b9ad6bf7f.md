# Buffer Management (Cont.)

Database buffers are generally implemented in virtual memory in spite of some drawbacks:

+   - When operating system needs to evict a page that has been modified, the page is written to swap space on disk.
+   - When database decides to write buffer page to disk, buffer page may be in swap space, and may have to be read from swap space on disk and output to the database on disk, resulting in extra I/O!
+     - Known as **dual paging** problem.
+   - Ideally when OS needs to evict a page from the buffer, it should pass control to database, which in turn should
+     1. Output the page to database instead of to swap space (making sure to output log records first), if it is modified
+     2. Release the page from the buffer, for the OS to use

Dual paging can thus be avoided, but common operating systems do not support such functionality.