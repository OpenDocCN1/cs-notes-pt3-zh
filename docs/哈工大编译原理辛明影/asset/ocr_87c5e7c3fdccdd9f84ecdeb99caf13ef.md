# 9.2.3 局部数据的组织

在SPARC/Solaris工作站上下面两个结构的size 分别是24和16，为什么不一样？

```
typedef struct _a{
    char c1;  0
    long i;  4
    char c2;  8
    double f;  16
}a;
```

```
typedef struct _b{
    char c1;  0
    char c2; 1
    long i;  4
    double f;8
}b;
```