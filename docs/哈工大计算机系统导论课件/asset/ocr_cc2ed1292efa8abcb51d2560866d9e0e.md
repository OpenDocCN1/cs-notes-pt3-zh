# # “Do-While” 循环的汇编实现



```
```c
long pcount_goto
(unsigned long x) {
long result = 0;
loop:
result += x & 0x1;
 x >>= 1;
 if(x) goto loop;
 return result;
}
```
```

| 寄存器 | 用法 |
|--------|------|
| %rdi | 参数 x |
| %rax | 返回值 |

```
```asm
movl $0, %eax  # result = 0
.L2:  # loop:
movq %rdi, %rdx
andl $1, %rdx  # t = x & 0x1
addq %rdx, %rax  # result += t
shrq %rdi  # x >>= 1
jne .L2  # if (x) goto loop
rep; ret
```
```