# Weak Levels of Consistency

+   - **Degree-two consistency**: differs from two-phase locking in that S-locks may be released at any time, and locks may be acquired at any time
+     - X-locks must be held till end of transaction
+     - Serializability is not guaranteed, programmer must ensure that no erroneous database state will occur
+   - **Cursor stability**:
+     - For reads, each tuple is locked, read, and lock is immediately released
+     - X-locks are held till end of transaction
+     - Special case of degree-two consistency