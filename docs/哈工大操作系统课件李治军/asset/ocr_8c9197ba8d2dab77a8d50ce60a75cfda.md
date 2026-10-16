# after_page_tables //设置了页表之后

setup是进入保护模式，head是进入之后的初始化

```
after_page_tables:
    pushl $0    pushl $0    pushl $0    pushl $L6
    pushl $_main    jmp set_paging
L6:    jmp L6
setup_paging: 设置页表    ret
```

将来学到!

简单的几句程序，控制流却很复杂

setup_paging执行ret后？会执行函数main()

进入main()后的栈为0, 0, 0, L6

main()函数的三个参数是0, 0, 0

main()函数返回时进入L6, 死循环...

C执行func(p1,p2,p3)

| |
| p3 |
| p2 |
| p1 |
| 返回地址 |

![](bbox=[0.92, 0.78, 0.99, 0.92])