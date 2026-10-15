# Setup code in swap_add

swap_add:

```
1  pushl %ebp
    Save old %ebp
```

```
2  movl %esp,%ebp
    Set %ebp as frame pointer
```

# Stack frame for caller

| | |
|---|---| 
| 24 | Saved %ebp | 
| 20 | arg2(1057) | 
| 16 | arg1(534) | 
| 12 | yp(&arg2) | 
| 8 | xp(&arg1) | 
| 4 | Return Addr | 
| 0 | Saved %ebp |

![](bbox=[0.8, 0.32, 0.95, 0.68])

Stack frame for swap_add