# # Conditional Branch Example (Old Style)

+   - **Generation**

`shark<> gcc -Og -S -fno-if-conversion cond`

```
long absdiff
(long x, long y)
{
  long result;
  if (x > y)
    result = x-y;
  else
    result = y-x;
  return result;
}
```

```
absdiff:
    cmpq    %rsi, %rdi    # x:y
    jle     .L4
    movq    %rdi, %rax
    subq    %rsi, %rax
    ret
.L4:             # x <= y
    movq    %rsi, %rax
    subq    %rdi, %rax
    ret
```

| Register | Use(s) |
|---|---|
| `%rdi` | Argument x |
| `%rsi` | Argument y |
| `%rax` | Return value |

![](bbox=[0.764, 0.112, 1.0, 0.217])