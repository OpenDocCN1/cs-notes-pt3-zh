# 进程对象描述图

| 对象头部属性 | Type: Process |
| 对象体属性 | 进程标识（Process id）
访问令牌（Access token）
基础优先级（Base priority）
缺省亲和处理机（Default processor affinity）
配额限制（Quota limits）
执行时间（Execution time）
输入输出计数（I/O counters）
执行调试端口（Exception/debugging ports）
退出状态（exit status） |
| 服务 | 创建进程（Create process）
打开进程（Open process）
查询进程信息（Query process information）
设置进程信息（Set process information）
当前进程（Current process）
终止进程（Terminate process）
分配释放虚拟存储（Allocate/free virtual memory）
读/写虚拟存储（Read/write virtual memory）
保护虚拟存储（Protect virtual memory）
加锁/开锁虚存（Lock/unlock virtual memory）
查询虚拟存储（Query virtual memory）
刷新虚拟存储（Flush virtual memory） |