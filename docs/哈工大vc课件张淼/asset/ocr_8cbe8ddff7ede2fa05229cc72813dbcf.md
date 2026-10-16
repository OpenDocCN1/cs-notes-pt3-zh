# 字符串常量

字符串和宏定义一行写不下需要续行时需用续行符\。

```
"this is a string!\
mnp"
```

```
#define CONTAINING_RECORD(address, type, field) ((type *)(\
(PCHAR)(address) - \
(UINT_PTR)(&((type *)0)->field)))
```