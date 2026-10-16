# 4.2.2 ORACLE数据库实例创建

关闭数据库过程与启动相反，关闭数据文件，关闭日志文件，关闭控制文件，关闭实例并释放资源。关闭数据库命令：

```
SHUTDOWN
[NORMAL | TRANSACTIONAL | IMMEDIATE | ABORT];
```

| SHUTDOWN | ABORT | IMMEDIATE | TRANSACTIONAL | NORMAL |
|---|---|---|---|---|
| 允许新的连接 | NO | NO | NO | NO |
| 等待用户结束会话 | NO | NO | NO | YES |
| 等待事务结束 | NO | NO | YES | YES |
| 产生检查点并关闭数据文件 | NO | YES | YES | YES |