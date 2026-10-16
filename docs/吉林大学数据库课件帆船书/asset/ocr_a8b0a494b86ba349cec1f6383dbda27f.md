# ARIES Data Structures: Page LSN

+   - Each page contains a **PageLSN** which is the LSN of the last log record whose effects are reflected on the page
+     - To update a page:
+       - X-latch the page, and write the log record
+       - Update the page
+       - Record the LSN of the log record in PageLSN
+       - Unlock page
+     - To flush page to disk, must first S-latch page
+       - Thus page state on disk is operation consistent
+         - Required to support physiological redo
+     - PageLSN is used during recovery to prevent repeated redo
+       - Thus ensuring idempotence