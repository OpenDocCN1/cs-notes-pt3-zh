# 编译器生成的代码移动 (-O1)

```
```c
void set_row(double *a, double *b,
    long i, long n)
{
    long j;
    for (j = 0; j < n; j++)
        a[n*i+j] = b[j];
}
```
```

```
```c
long j;
long ni = n*i;
double *rowp = a+ni;
for (j = 0; j < n; j++)
    *rowp++ = b[j];
```
```

```
```asm
set_row:
        testq   %rcx, %rcx             # Test n
        jle     .L1                    # If 0, goto done
        imulq   %rcx, %rdx             # ni = n*i
        leaq    (%rdi,%rdx,8), %rdx    # rowp = A + ni*8
        movl    $0, %eax               # j = 0
.L3:                                    # loop:
        movsd   (%rsi,%rax,8), %xmm0   # t = b[j]
        movsd   %xmm0, (%rdx,%rax,8)   # M[A+ni*8 + j*8] = t
        addq    $1, %rax               # j++
        cmpq    %rcx, %rax              # j:n
        jne     .L3                    # if !=, goto loop
.L1:                                    # done:
        rep ; ret
```
```