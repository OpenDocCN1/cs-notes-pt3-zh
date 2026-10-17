# # Callee-Saved Example #2

```
```c
long call_incr2(long x) {
    long v1 = 15213;
    long v2 = incr(&v1, 3000);
    return x+v2;
}
```
```

```
```asm
call_incr2:
    pushq   %rbx
    subq    $16, %rsp
    movq    %rdi, %rbx
    movq    $15213, 8(%rsp)
    movl    $3000, %esi
    leaq    8(%rsp), %rdi
    call    incr
    addq    %rbx, %rax
    addq    $16, %rsp
    popq    %rbx
    ret
```
```

# ## Initial Stack Structure

![](bbox=[0.56, 0.23, 0.82, 0.42])

# ## Resulting Stack Structure

![](bbox=[0.56, 0.6, 0.82, 0.85])