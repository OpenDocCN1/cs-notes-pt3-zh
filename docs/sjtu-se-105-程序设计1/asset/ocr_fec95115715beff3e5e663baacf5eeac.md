# 5 循环体

+   - 依赖图处理：
+     - 现在依赖图为空，编程完成
+     - 棘手情况：
+       - 依赖图中有环
+       - 例如：

```
foo_helper(int bar, int baz){
    ...
    foo_helper(baz-1, bar-1);
}
```