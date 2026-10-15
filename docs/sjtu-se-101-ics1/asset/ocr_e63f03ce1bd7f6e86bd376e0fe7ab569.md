# Stack Corruption Detection

```
1 echo:
2     pushl %ebp
3     movl %esp, %ebp
4     pushl %ebx
5     subl $20, %esp
6     movl %gs:20, %eax    Retrieve canary
7     movl %eax, -8(%ebp)   Store on stack
8     xorl %eax, %eax       Zero out register
9     leal -16(%ebp), %ebx  Compute buf as %ebp-16
10    movl %ebx, (%esp)     Store buf at top of stack
11    call gets            Call gets
12    movl %ebx, (%esp)     Store buf at top of stack
13    call puts            Call puts
```