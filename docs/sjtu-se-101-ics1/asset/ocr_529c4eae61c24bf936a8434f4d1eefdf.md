# Y86 Instructions

IA32 code
Y86 code

```
9 .L35:
10   addl (%ecx),%eax   add *Start to sum
11   addl $4,%ecx        Start++
12   decl %edx           Count--
13   jnz .L35            Stop when 0
14 .L34:
15   movl %ebp,%esp
16   popl %ebp
•   ret

9 Loop:
10   mrmovl (%ecx),%esi
11   addl %esi,%eax
12   irmovl $4,%ebx
13   addl %ebx,%ecx
14   irmovl $-1,%ebx
15   addl %ebx,%edx
16   jne Loop
17 End:
18   rrmovl %ebp,%esp
19   popl %ebp
20   ret
```