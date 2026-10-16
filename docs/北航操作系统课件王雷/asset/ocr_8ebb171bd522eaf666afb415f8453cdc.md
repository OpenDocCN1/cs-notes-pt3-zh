# OS

# main.o

```
0: 55              push %ebp
1: 89 e5            mov %esp,%ebp
3: 83 ec 08         sub $0x8,%esp
6: e8 fc ff ff ff   call 7 <main+0x7>
b: 89 c0            mov %eax,%eax
d: 89 45 fc         mov %eax,0xfffffff(%ebp)
10: 83 ec 0c        sub $0xc,%esp
13: ff 75 fc        pushl 0xfffffff(%ebp)
16: e8 fc ff ff ff   call 17 <main+0x17>
1b: 83 c4 10        add $0x10,%esp
1e: 89 c0           mov %eax,%eax
20: a3 00 00 00 00   mov %eax,0x0
25: 83 ec 0c        sub $0xc,%esp
28: 68 00 00 00 00   push $0x0
2d: e8 fc ff ff ff   call 2e <main+0x2e>
32: 83 c4 10        add $0x10,%esp
35: c9             leave
36: c3             ret
37: 90             nop
```

.offset = 0x7
r_symbol = read_something
r_type = R_386_PC32