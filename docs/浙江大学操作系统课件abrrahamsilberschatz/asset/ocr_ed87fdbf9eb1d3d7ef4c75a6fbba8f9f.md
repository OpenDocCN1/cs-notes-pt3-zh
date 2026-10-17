# # 12.8 Log Structured File Systems 日志结构文件系统

+   Log structured (or journaling) file systems record each update to the file system as a **transaction**. 日志结构文件系统记录每一次更新文件系统事务

+   All transactions are written to a log. A transaction is considered **committed** once it is written to the log. However, the file system may not yet be updated. 所有的事务都被记录在log中，一个事务被认为是记录在log中的一个提交（委托），然而文件系统可能仍然没有更新。

+   The transactions in the log are asynchronously written to the file system. When the file system is modified, the transaction is removed from the log. 日志中的事务异步写入文件系统，当文件系统被修改，这个事务从日志中删除。

+   If the file system crashes, all remaining transactions in the log must still be performed. 如果文件系统崩溃，在日志所有保存事务仍然可执行（恢复）