# Setup code in swap_add

```
swap_add:
1 pushl %ebp
    Save old %ebp
2 movl %esp,%ebp
    Set %ebp as frame pointer
3 pushl %ebx
    Save %ebx
```

Stack frame for caller

|  | |
|---|---| 
| 24 | Saved %ebp |
| 20 | arg2(1057) |
| 16 | arg1(534) |
| 12 | yp(&arg2) |
| 8 | xp(&arg1) |
| 4 | Return Addr |
| 0 | Saved %ebp |
| -4 | Saved %ebx |

%ebp

%esp

Stack frame for swap_add