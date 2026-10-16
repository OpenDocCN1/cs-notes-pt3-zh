# 共同修改信号量引出的问题

初始情况

```
empty = -1;
```

这是什么含义？

生产者P₁

```
register = empty;
register = register - 1;
empty = register;
```

生产者P₂

```
register = empty;
register = register - 1;
Empty = register;
```

```
Producer(item) {
  P(empty);
  ...
}
```

一个可能的执行(调度)

+   P₁.register = empty;
+   P₁.register = P₁.register - 1;
+   P₂.register = empty;
+   P₂.register = P₂.register - 1;
+   empty = P₁.register;
+   empty = P₂.register;

最终的empty等于多少?对吗?