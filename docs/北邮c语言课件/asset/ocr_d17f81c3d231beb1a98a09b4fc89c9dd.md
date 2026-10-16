# 3、求字节运算符： sizeof

+   - 作用：求得变量或某种数据类型所需的字节数。
+   - 形式有两种：
+     - sizeof 变量名
+     - sizeof (类型名)
+   - 结果为整型数。

# 例如

```
int a;
float x;
printf(" %d, %d" , sizeof a, sizeof x);
printf(" %d, %d" , sizeof(int), sizeof(float));
```

以上两个printf语句结果均为 2, 4 。