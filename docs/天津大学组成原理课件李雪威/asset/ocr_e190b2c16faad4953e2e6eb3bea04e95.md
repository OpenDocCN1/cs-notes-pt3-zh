# # Small Exercise

```
```c
long add5(long b0, long b1, long b2, long b3, long b4) {
  return b0+b1+b2+b3+b4;
}

long add10(long a0, long a1, long a2, long a3, long a4, long a5,
           long a6, long a7, long a8, long a9) {
  return add5(a0, a1, a2, a3, a4)+
         add5(a5, a6, a7, a8, a9);
}
```
```

```
```asm
add10:
  pushq   %rbp
  pushq   %rbx
  movq    %r9, %rbp
  call    add5
  movq    %rax, %rbx
  movq    48(%rsp), %r8
  movq    40(%rsp), %rcx
  movq    32(%rsp), %rdx
  movq    24(%rsp), %rsi
  movq    %rbp, %rdi
  call    add5
  addq    %rbx, %rax
  popq    %rbx
  popq    %rbp
  ret
```
```

```
```asm
add5:
  addq    %rsi, %rdi
  addq    %rdi, %rdx
  addq    %rdx, %rcx
  leaq    (%rcx,%r8), %rax
  ret
```
```

![](bbox=[0.713, 0.168, 0.977, 0.758])

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

59