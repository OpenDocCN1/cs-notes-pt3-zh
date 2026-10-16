# 13.5 Transforming I/O Requests to Hardware Operations

Consider reading a file from disk for a process:

+   - Determine device holding file
+   - Translate name to device representation
+   - Physically read data from disk into buffer
+   - Make data available to requesting process
+   - Return control to process