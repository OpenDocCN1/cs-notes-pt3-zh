# Data Dependencies: 2 Nop's

```
# demo-h2.ys
0x000: irmovl $10,%edx
0x006: irmovl $3,%eax
0x00c: nop
0x00d: nop
0x00e: addl %edx,%eax
0x010: halt
```

1 2 3 4 5 6 7 8 9 10
F D E M W
F D E M W
F D E M W
F D E M W
F D E M W
F D E M W

Cycle 6

Write Back
R[%eax] ← 3

Decode
val ← R[%edx] = 10
val ← R[%eax] = 0
Error