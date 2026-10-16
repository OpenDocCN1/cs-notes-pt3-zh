# 理解Swap()

Registers

%rdi 0x120
%rsi 0x100
%rax 123
%rdx 456

Memory

Address
0x120
0x118
0x110
0x108
0x100
456
123

```
swap:
    movq (%rdi), %rax # t0 = *xp
    movq (%rsi), %rdx # t1 = *yp
    movq %rdx, (%rdi) # *xp = t1
    movq %rax, (%rsi) # *yp = t0
    ret
```