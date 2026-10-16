# 数据传送

+   无符号数的条件传送

CMOVE/CMOVZ      等于/零      ZF = 1

CMOVNE/CMOVNZ    不等于/不为零    ZF = 0

CMOVP/CMOVPE     奇偶校验    PF = 1

例子：

```
cmova %ebx,%eax
```

```
cmoval %ebx, %eax
```