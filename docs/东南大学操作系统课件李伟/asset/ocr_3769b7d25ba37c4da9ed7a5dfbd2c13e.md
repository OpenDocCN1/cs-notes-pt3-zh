# # Race Conditions

+   - Concurrent access of same variable by multiple threads
+     - Read/Write conflict
+     - Write/Write conflict
+   - Most common error in concurrent programs
+   - May not be apparent at all times
+   - How to avoid data races?
+     - Local storage
+     - Control shared access with **critical regions**