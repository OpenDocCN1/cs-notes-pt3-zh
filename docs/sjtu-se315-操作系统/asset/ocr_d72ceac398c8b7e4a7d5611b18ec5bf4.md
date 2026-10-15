# Xv6 disk driver design & Implementation

+   - Design Overview
+     - Support an IDE driver
+     - Use I/O Instructions instead of Memory Mapped I/O
+       - in, out
+     - Asynchronous I/O model
+       - Use a simple queue of I/O request
+       - Use interrupt to notify the available of data