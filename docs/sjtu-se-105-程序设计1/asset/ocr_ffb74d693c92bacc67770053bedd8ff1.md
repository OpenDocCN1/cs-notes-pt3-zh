# 从错误中恢复

+   - clean_up_mess() 现在很简单了
+     - 并且能够工作

```
void clean_up_mess()
{
    ts.ignore(print);
}
```

+   - 注意我们所做的和我们如何做的区别:
+     - clean_up_mess() 是用户看到的，它清理了混乱情况
+       - 用户对如何清理并不感兴趣
+     - ts.ignore(print) 是我们实现clean_up_mess()的方式
+       - 我们可以修改或完善清理的方式，而不影响用户