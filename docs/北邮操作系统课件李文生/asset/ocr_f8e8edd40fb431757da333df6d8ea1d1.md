# 13.3 Application I/O Interface

+   - I/O system calls encapsulate device behaviors in generic classes
+   - Devices vary in many dimensions
+     - Character-stream or block
+     - Sequential or random-access
+     - Synchronous or asynchronous
+     - Sharable or dedicated
+     - Speed of operation
+     - read-write, read only, or write only
+   - Device-driver layer hides differences among I/O controllers from kernel