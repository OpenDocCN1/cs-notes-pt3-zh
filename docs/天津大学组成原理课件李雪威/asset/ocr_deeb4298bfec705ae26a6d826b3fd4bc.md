# Example: Calling `incr` #5b

```
```c
long call_incr() {
    long v1 = 15213;
    long v2 = incr(&v1, 3000);
    return v1+v2;
}
```
```

# Updated Stack Structure

![](bbox=[0.573, 0.253, 0.837, 0.447])

```
```asm
call_incr:
  subq   $16, %rsp
  movq   $15213, 8(%rsp)
  movl   $3000, %esi
  leaq   8(%rsp), %rdi
  call   incr
  addq   8(%rsp), %rax
  addq   $16, %rsp
  ret
```
```

| Register | Use(s) |
|---|---|
| `%rax` | Return value |

# Final Stack Structure

![](bbox=[0.573, 0.755, 0.837, 0.892])