# 名字解析

```
void fooBar( int *ia, int sz )
{
    for (int i=0; i<sz; ++i) ... // ok
    for (int i=0; i<sz; ++i) ... // ok: 不同的 i
    for (int i=0; i<sz; ++i) ... // ok: 不同的 i
}
```