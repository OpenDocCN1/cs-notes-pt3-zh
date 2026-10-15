# Jump Instructions

```
1   xorl  %eax, %eax      Set %eax to 0
2   jmp   .L1             Goto .L1
3   movl  (%eax), %edx    Null pointer dereference
4   .L1:
5   popl  %edx
```