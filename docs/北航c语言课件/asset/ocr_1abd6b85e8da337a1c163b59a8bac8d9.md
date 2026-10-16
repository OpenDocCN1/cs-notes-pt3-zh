例：若有：`int i;` `float f;` `double d;` `long e;`

试判断表达式 `3 + 'b' + i*f - d/e` 的类型

类型推导：`3 + 'b'` → `int`；`i*f` → `float`；中间结果为 `float`；`d/e` → `double`；最终结果为 `double`。

例：如果 `int a=5,b=2;`

```
double x;
x=a/b;
printf(" x=%f",x);
```

输出结果是什么？

`x=2.000000`