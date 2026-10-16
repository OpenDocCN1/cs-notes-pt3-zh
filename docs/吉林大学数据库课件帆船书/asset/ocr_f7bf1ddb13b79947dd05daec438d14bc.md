# Indexing Strings

+   - Variable length strings as keys
+     - Variable fanout
+     - Use space utilization as criterion for splitting, not number of pointers
+   - Prefix compression
+     - Key values at internal nodes can be prefixes of full key
+       - Keep enough characters to distinguish entries in the subtrees separated by the key value
+         - E.g. “Silas” and “Silberschatz” can be separated by “Silb”
+     - Keys in leaf node can be compressed by sharing common prefixes