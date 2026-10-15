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

![](bbox=[0.431, 0.217, 0.984, 0.578])

+   - If instruction follows too closely after one that writes register, slow it down
+   - Hold instruction in decode
+   - Dynamically inject **nop** into execute stage