# 有那么一次时钟中断

```
main() {
    mov __NR_fork, %eax
    int 0x80
100: mov %eax, res
    cmpl res,0
    jne 208
200: printf("A")
    jmp 200
208: ... 300:printf("B")
        jmp 300
308: wait()
}
```

B的用户栈

EFLAGS

300

call do_timer压的栈

```
do_timer(...) {
    current->counter=0; schedule(); }
```