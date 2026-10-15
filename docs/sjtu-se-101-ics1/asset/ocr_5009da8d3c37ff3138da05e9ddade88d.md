# Y86 Object Program

```
15    Main: pushl %ebp
16          rrmovl %esp,%ebp
17          irmovl $4,%eax
18          pushl %eax        # Push 4
19          irmovl array,%edx
20          pushl %edx        # Push array
21          call Sum          # Sum(array, 4)
22          rrmovl %ebp,%esp
23          popl %ebp
24          ret
25
```