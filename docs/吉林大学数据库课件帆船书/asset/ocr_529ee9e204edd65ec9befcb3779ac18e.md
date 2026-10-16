# ARIES

+   - ARIES is a state of the art recovery method
+     - Incorporates numerous optimizations to reduce overheads during normal processing and to speed up recovery
+     - The recovery algorithm we studied earlier is modeled after ARIES, but greatly simplified by removing optimizations
+   - Unlike the recovery algorithm described earlier, ARIES
+     1. Uses **log sequence number (LSN)** to identify log records
+        - Stores LSNs in pages to identify what updates have already been applied to a database page
+     2. Physiological redo
+     3. Dirty page table to avoid unnecessary redos during recovery
+     4. Fuzzy checkpointing that only records information about dirty pages, and does not require dirty pages to be written out at checkpoint time
+        - More coming up on each of the above ...