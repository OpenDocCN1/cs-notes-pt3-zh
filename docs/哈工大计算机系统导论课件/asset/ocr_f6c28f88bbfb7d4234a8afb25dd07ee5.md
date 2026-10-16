# # 代码块(x == 5, x == 6, default)

| 寄存器 | 用途 |
|--------|------|
| %rdi | 参数x |
| %rsi | 参数y |
| %rdx | 参数z |
| %rax | 返回值 |

```
```c
switch(x) {
...
case 5: // .L7
case 6: // .L7
w -= z;
break;
default: // .L8
w = 2;
}
```
```

```
```assembly
.L7:  # Case 5,6
movl $1, %eax # w = 1
subq %rdx, %rax # w -= z
ret
.L8:  # Default:
movl $2, %eax # 2
ret
```
```