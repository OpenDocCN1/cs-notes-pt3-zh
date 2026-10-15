# Lockset

# Locking Discipline

+   - A programming policy that ensures the absence of data races
+     - e.g. “every variable shared between threads is protected by a mutual exclusion lock”

# Principle

+   - Check all shared memory accesses follow a consistent lock discipline
+     - monitors all reads and writes, and infer the protection relation from the execution history