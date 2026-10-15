# IntSet示例

```
void IntSet::remove(int v){
    int victim = indexOf(v);
    if (victim != MAXELTS) {
        elts[victim] = elts[numElts-1];
        numElts--;
    } else {
        throw v;
    }
}
```

+   - 这就是完整的IntSet版本了吗？