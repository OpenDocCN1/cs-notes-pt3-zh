# 11.8* Log Structured File Systems

+   - **Log structured** (or journaling) file systems record each update to the file system as a **transaction**.
+   - All transactions are written to a **log**. A transaction is considered **committed** once it is written to the log. However, the file system may not yet be updated.
+   - The transactions in the log are asynchronously written to the file system. When the file system is modified, the transaction is removed from the log.
+   - If the file system crashes, all remaining transactions in the log must still be performed.