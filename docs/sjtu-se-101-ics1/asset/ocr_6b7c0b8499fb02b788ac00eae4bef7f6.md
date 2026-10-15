# Permutation

```
_permute:
    pushl    %ebp
    movl     %esp, %ebp
    subl     $40, %esp
    cmpl     $0, 16(%ebp)      # k == 0 ?
    jne      L2
    movl     $0, -12(%ebp)     # i = 0
    jmp      L3
```