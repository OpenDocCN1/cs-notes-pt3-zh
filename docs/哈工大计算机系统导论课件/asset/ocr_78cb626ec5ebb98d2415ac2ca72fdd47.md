# "Do-While" 循环示例

+   - 计算参数x中1的个数 ("popcount")
+   - 使用条件分支实现继续循环或退出循环

C代码

goto版本

```
long pcount_do (unsigned long x)
{
    long result = 0;
    do {
        result += x & 0x1;
        x >>= 1;
    } while (x);
    return result;
}
```

```
long pcount_goto
(unsigned long x) {
    long result = 0;
    loop:
    result += x & 0x1;
    x >>= 1;
    if(x) goto loop;
    return result;
}
```