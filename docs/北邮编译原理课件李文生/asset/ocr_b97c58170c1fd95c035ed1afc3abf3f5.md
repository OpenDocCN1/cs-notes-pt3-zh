# 三、记录声明的处理

+   文法
+   P→ D; S
+   D→ D; D
+   D→ id: T
+   D→ proc id; D; S
+   T→ record D end

定位操作：
创建符号表
保存记录中各域的信息

重定位操作：
将各域的总域宽作为该记录型的域宽，
返回记录声明所在过程的符号表

# 翻译方案3

```
T→ record L D end { T.type=record(top(tableptr)); T.width=top(offset); pop(tableptr); pop(offset) }
```

```
L→ε { t=mktable(nil); push(t, tableptr); push(0, offset) }
```