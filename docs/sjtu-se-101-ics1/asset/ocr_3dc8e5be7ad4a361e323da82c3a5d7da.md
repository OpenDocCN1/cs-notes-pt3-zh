# Line Replacement on Misses

+   - Check the cache line of the set indicated by the set index bits
+     - If the cache line valid, it must be evicted
+   - Retrieve the requested block from the next level
+   - Current line is replaced by the newly fetched line