# 基于Log的备份

+   - To ensure atomicity despite failures, we first output information describing the modifications to stable storage without modifying the database itself.
+   - log-based recovery