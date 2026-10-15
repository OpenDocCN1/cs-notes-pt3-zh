# Setup code in swap_add

```
swap_add:
```

```
1 pushl %ebp
```

*Save old %ebp*

# Stack frame for caller

| Offset | Content | |
|---|---|---|
| 0 | Saved %ebp | %ebp |
| -4 | arg2(1057) | |
| -8 | arg1(534) | |
| -12 | yp(&arg2) | |
| -16 | xp(&arg1) | |
| -20 | Return Addr | |
| -24 | Saved %ebp | %esp |