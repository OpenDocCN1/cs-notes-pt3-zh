# 线程对象描述图

| 对象头部属性 属性 | 类型： 线程（Type: thread） |
|---|---|
| 属性 | 客户标识（client id）
线程上下文（thread context）
动态优先级（dynamic priority）
处理机亲和掩码（thread processor affinity）
已执行时间（thread execution time）
警觉状态（alert status）
挂起计数（suspension count）
非角色令牌（impersonation token）
终止端口（termination port）
终止状态（exit status） |
| 服务 | 创建线程（Create thread）
打开线程（Open thread）
查询线程状态（Query thread information）
设置线程状态（Set thread information）
当前线程（Current thread）
终止线程（Terminate thread）
取上下文（Get context）
置上下文（Set context）
挂起（Suspend）
恢复（Resume）
警示线程（Alert thread）
测试线程警示（Test thread alert）
注册终止端口（Register termination port） |