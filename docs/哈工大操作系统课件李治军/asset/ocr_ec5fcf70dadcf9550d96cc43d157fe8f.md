# 竞争条件(Race Condition)

🟥 竞争条件：和调度有关的共享数据语义错误

```
第一次执行
P₁.register = empty;
P₁.register = P₁.register - 1;
P₂.register = empty;
P₂.register = P₂.register - 1;
empty = P₁.register;
empty = P₂.register;
```

```
第一次执行
P₁.register = empty;
P₁.register = P₁.register - 1;
empty = P₁.register;
P₂.register = empty;
P₂.register = P₂.register - 1;
empty = P₂.register;
```

+   - 错误由多个进程并发操作共享数据引起
+   - 错误和调度顺序有关，难于发现和调试
+     - 问题：右面的图这两个人的方法有效果吗？

![](bbox=[0.692, 0.195, 0.899, 0.571])

![](bbox=[0.904, 0.744, 0.985, 0.886])