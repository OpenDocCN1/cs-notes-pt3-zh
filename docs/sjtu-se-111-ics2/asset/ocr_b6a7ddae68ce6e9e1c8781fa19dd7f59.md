# Data Dependencies: 2 Nop's

![](bbox=[0.374, 0.095, 0.927, 0.458])

```
```asm
# demo-h2.ys
0x000:irmovl $10,%edx
0x006:irmovl $3,%eax
0x00c:nop
0x00d:nop
```
```

bubble

```
```asm
0x00e:addl %edx,%eax
0x010:halt
```
```

![](bbox=[0.616, 0.476, 0.741, 0.525])

| Write Back |
|---|
| W_dstE=%eax |
| W_valE=3 |

| Decode |
|---|
| srcA=%edx |
| srcB=%eax |