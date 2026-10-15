# 从错误中恢复

+   - 第一次尝试

```
void clean_up_mess()
{
    while (true) {        // skip until we find a print
        Token t = ts.get();
        if (t.kind == print) return;
    }
}
```

+   - 但是，这不能很好地工作。为什么？

+   - 考虑输入为：1@$z; 1+3;

+   - 当因为碰到了@而调用clean_up_mess()时，会调用get，此时得到$，再次是一个“Bad token”，于是错误抛给了main，程序终止

+   - 在处理错误的代码中不能产生新的错误