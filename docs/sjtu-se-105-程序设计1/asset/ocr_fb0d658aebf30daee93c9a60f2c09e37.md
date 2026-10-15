+   - 将%添加到Token集合中
+   - 将double转型为int，以支持%

```
case '%':
{
    double d = term();
    int i1 = int(left);
    if (i1 != left) error ("left-hand operand of % not int");
    int i2 = int(d);
    if (i2 != d) error ("right-hand operand of % not int");
    if (i2 == 0) error("%: divide by zero");
    left = i1%i2;
    t = ts.get();
    break;
}
```