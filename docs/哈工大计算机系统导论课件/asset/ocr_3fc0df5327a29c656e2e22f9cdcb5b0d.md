# 2.1 布尔指令——XOR

| X | Y | X ⊕ Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

```
mov $0xb5, %al
xor $0, %al #al=0xb5
mov $0xcc, %al
xor $0, %al #al=0xcc
```

CF=0, OF=0
ZF=0, SF=1, PF=0

CF=0, OF=0
ZF=0, SF=1, PF=1