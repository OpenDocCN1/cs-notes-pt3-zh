# 潜在风险

+   - 下面的代码将出现相同的情况：

```
void foo()
{
    IntSet s(5);
    s.insert(7);
    {
        IntSet x = s;
    }
    s.query(7); // Undefined!
}
```