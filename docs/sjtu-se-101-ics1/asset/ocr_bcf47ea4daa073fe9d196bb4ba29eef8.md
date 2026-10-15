# While Loop Translation

| Register usage |
|---|---|---|
| Register | Variable | Initially |
| %edx | nmi | n-1 |
| %ebx | val | 1 |
| %ecx | nval | 1 |

```
1. movl 8(%ebp), %eax
2. movl $1, %ebx
3. movl $1, %ecx
4. cmpl %eax, ebx
5. jge .L9
6. lea -1(%eax), %edx
7. .L10:
8. lea (%ecx, %ebx), %eax
9. movl %ecx, %ebx
10. movl %eax, %ecx
11. decl %edx
12. jnz .L10
13. .L9:
```