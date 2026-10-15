# ◆ 5 循环体

+   • 依赖图处理：
+     - bar 和 baz 互相依赖：`bar ↔ baz`
+     - 不能先更新其中任何一个
+     - 解决办法：
+       • 引入“影子”变量，在赋值之前保存“新”值

```
int bar_new = baz-1;
int baz_new = bar-1;
bar = bar_new;
baz = baz_new;
```