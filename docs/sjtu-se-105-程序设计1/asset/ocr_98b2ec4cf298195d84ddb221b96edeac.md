+   - 在这样的表示法和不变式下，可以很容易地写出各个方法
+   - 从最容易的size()开始：
+   - 由于不变式要求numElts 始终表示集的尺寸，因此可以立即返回它：

```
int IntSet::size()
{
    return numElts;
}
```