# Lockset based Detectors

The definition of data race:

+   1. a pair of accesses to the same memory location
+   2. at least one access is a write
+   3. No lock protects all accesses to the same data