# 程序是什么?就是人的思维的C表达

```
main() {
    mov __NR_fork, %eax
    int 0x80
100: mov %eax, res
    cmpl res,0
    jne 208
200: printf("A")
    jmp 200
208: ...
304: wait()
}

把自己变成计算机跑一遍
AB.C
```

![](bbox=[0.92, 0.7, 0.99, 0.9])