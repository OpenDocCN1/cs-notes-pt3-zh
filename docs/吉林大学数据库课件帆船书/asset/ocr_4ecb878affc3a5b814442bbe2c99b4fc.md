# Log Record Buffering

+   - **Log record buffering**: log records are buffered in main memory, instead of of being output directly to stable storage.
+     - Log records are output to stable storage when a block of log records in the buffer is full, or a **log force** operation is executed.

+   - Log force is performed to commit a transaction by forcing all its log records (including the commit record) to stable storage.

+   - Several log records can thus be output using a single output operation, reducing the I/O cost.