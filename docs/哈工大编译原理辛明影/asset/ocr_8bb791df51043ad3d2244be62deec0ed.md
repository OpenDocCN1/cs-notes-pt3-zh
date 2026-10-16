# # 9.2.3 局部数据的组织

在X86/Linux机器的结果和SPARC/Solaris工作站不一样，是20和16。

```
typedef struct _a{
char c1; 0
long i; 4
char c2; 8
double f; 12
}a;
```

```
typedef struct _b{
char c1; 0
char c2; 1
long i; 4
double f;8
}b;
```