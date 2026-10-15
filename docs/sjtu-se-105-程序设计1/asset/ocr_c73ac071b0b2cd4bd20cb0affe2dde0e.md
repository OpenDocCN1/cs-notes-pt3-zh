# 从错误中恢复

+   - 将读入和计算循环放入calculate() 中，可以简化代码

```
void calculate()
{
    while (cin) {
        cout << prompt;
        Token t = ts.get();
        while (t.kind == print) t=ts.get();    // first discard all "prints"
        if (t.kind == quit) return;            // quit
        ts.putback(t);
        cout << result << expression() << endl;
    }
}
```