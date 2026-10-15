# savings成员函数和 < 操作符

```
double Sale::savings(const Sale& other) const
{
    return (bill() - other.bill());
}
```

```
bool operator < (const Sale& first, const Sale& second)
{
    return (first.bill() < second.bill());
}
```

+   - 注意：它们都使用了成员函数bill()!