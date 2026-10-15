# Control for Return

| Condition | Trigger |
|---|---|
| Processing ret | IRET in { D_icode, E_icode, M_icode } |

```
#demo_retb
1: 0x026: ret
2: bubble
3: bubble
4: bubble
5: 0x00b: irmovl $5, %esi #return
```

![](bbox=[0.38, 0.42, 0.85, 0.7])

| Condition | F | D | E | M | W |
|---|---|---|---|---|---|
| Processing ret | stall | bubble | normal | normal | normal |