# One-writer Principle

+   - If each variable has only one writer
+     - Coordination becomes easier
+     - Concurrency and read-only data is easy
+     - Guide: Make as much data as you can have only a single writer
+   - Privatization: Make data private to a thread
+     - Allocate on thread stack
+     - Array indexed by thread_id()
+       - E.g. privateData[thread_id()]...
+   - Focus locking scheme on data shared read/write