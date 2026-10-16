# 2. f格式符——以浮点数形式输出实数。

(output the floating point real number)

(1) %f：不指定字段宽度,由系统自动指定，使整数部分全部如数输出，并输出6位小数。注意float型和double型数据的有效位数。

如： float x=123456.123;

```
printf("%f",x);
```

输出结果： 123456.125000