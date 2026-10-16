# “While”的实现#1

+   - “跳到中间”翻译法
+   - 使用选项 −Og

While版本

```
while (Test)
  Body
```

![](bbox=[0.378, 0.516, 0.547, 0.64])

goto版本

```
goto test;
loop:
  Body
test:
  if (Test)
    goto loop;
done:
```