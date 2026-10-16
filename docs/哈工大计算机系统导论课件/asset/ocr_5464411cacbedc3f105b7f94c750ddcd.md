# 调用Strlen

```
/* My version of strlen */
size_t strlen(const char *s)
{
    size_t length = 0;
    while (*s != '\0') {
        s++;
        length++;
    }
    return length;
}
```

# Strlen 性能

+   - 确定字符串长度的唯一方法是扫描它的整个长度，查找null字符

# 整体性能，长度为N的字符串

+   - N 次调用 strlen
+   - 需要时间 N, N-1, N-2, ..., 1
+   - 整体 O(N²) 性能