# # 16 X 16 Matrix Access

# ## Array Elements

+   - `int A[16][16];`

+   - Address `A + i * (C * K) + j * K`

+   - `C = 16, K = 4`

```
```c
/* Get element A[i][j] */
int fix_ele(fix_matrix A, size_t i, size_t j) {
    return A[i][j];
}
```
```

```
```asm
# A in %rdi, i in %rsi, j in %rdx
salq    $6, %rsi        # 64*i
addq    %rsi, %rdi      # A + 64*i
movl    (%rdi,%rdx,4), %eax  # M[A + 64*i + 4*j]
ret
```
```