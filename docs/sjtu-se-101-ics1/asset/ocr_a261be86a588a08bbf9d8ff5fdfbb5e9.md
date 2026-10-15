# Finishing code in swap_add

```
12 popl %ebx    Restore %ebx
13 movl %ebp, %esp    Restore %esp
```

Stack frame for caller

|  | |
|---|---| 
| 24 | Saved %ebp |
| 20 | arg2(534) |
| 16 | arg1(1057) |
| 12 | yp(&arg2) |
| 8 | xp(&arg1) |
| 4 | Return Addr |
| 0 | Saved %ebp |
| -4 | Saved %ebx |

%edx xp(= &arg1 = %ebp + 16)

%ecx yp(= &arg2 = %ebp + 20)

%ebx original value

%eax 1591

Stack frame for swap_add

![](bbox=[0.82, 0.65, 0.95, 0.75])