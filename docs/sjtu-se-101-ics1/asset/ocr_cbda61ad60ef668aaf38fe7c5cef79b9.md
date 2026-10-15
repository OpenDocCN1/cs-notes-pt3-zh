# Understanding x86-64 Stack Frame

```
swap_d:
    movq %rbx, -16(%rsp)    # save %rbx
    movslq %esi,%rbx
    movq %r12, -8(%rsp)    # save %r12
    movq %rdi, %r12
    leaq (%rdi,%rbx,8), %rdi
    subq $16, %rsp          # move stack frame
    leaq 8(%rdi), %rsi
    ...
    addq %rax, sum(%rip)
    movq (%rsp), %rbx       # restore %rbx
    movq 8(%rsp), %r12      # restore %r12
    addq $16, %rsp          # move stack frame
    ret
```

![](bbox=[0.68, 0.24, 0.95, 0.52])