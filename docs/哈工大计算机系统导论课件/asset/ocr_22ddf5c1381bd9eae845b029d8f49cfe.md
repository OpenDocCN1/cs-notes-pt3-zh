# 提高性能

```
void lower2(char *s)
{
    size_t i;
    size_t len = strlen(s);
    for (i = 0; i < len; i++)
        if (s[i] >= 'A' && s[i] <= 'Z')
            s[i] -= ('A' - 'a');
}
```

+   - 把调用 strlen 移动到循环外
+   - 因为结果 (strlen的长度) 不会在迭代中变化
+   - 代码移动的形式