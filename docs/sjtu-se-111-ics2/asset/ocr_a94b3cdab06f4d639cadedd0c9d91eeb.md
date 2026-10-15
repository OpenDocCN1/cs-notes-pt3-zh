# System Call Error Handling

+   - Unix system-level functions encounter an error
+     - typically return -1
+     - set the global integer variable `errno`
+       - to indicate what went wrong