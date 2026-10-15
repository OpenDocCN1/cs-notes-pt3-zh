# Assembly Code

n at %ebp+8, A at %ebp+12, i at %ebp+16, j at %ebp+20

```
1. movl 8(%ebp), %eax          Get n
2. sall $2, %eax               Compute 4*n
3. movl %eax, %edx             Copy 4*n
4. imull 16(%ebp), %edx        Compute 4*n*i
5. movl 20(%ebp), %eax         Get j
6. sall $2, %eax               Compute 4*j
7. addl 12(%ebp), %eax         Compute xA+4*j
8. movl (%eax,%edx), %eax      Read from xA+4*(n*i+j)
```