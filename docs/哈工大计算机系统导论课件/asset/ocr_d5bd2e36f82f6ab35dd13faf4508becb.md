# 编译生成的有符号数除代码

# C 函数

```
long idiv8(long x)
{
    return x/8;
}
```

# 编译生成的结果

```
testq %rax, %rax
js  L4
L3:
    sarq $3, %rax
    ret
L4:
    addq $7, %rax
    jmp  L3
```

# 解释

```
if x < 0
    x += 7;
# Arithmetic shift
return x >> 3;
```

+   - 使用了算术右移