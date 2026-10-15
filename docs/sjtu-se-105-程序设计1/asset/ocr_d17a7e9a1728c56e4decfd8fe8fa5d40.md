# 简单计算

```
int main()
{
    const double cm_per_inch = 2.54;    // 1英寸=2.54厘米
    int length = 1;                    // 英寸长度
    while (length != 0)                // 英寸长度如果为 0，则终止
    {
        cout << "Please enter a length in inches: ";
        cin >> length;
        cout << length << "in. = "
             << cm_per_inch*length << "cm.\n";
    }
}
```

+   - while语句重复执行，直至条件为假