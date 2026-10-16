# Linux汇编程序——两种格式的语法对比

（3）变址寻址

```
AT&T: movl %ecx,  var (%eax)
        movl %ecx,  array(, %eax,4)
        movl %ecx,  array(%ebx,%eax,8)
```

```
Intel: mov [eax + var], ecx
       mov [eax*4 + array], ecx
       mov [ebx + eax*8 + array], ecx
```

# 嵌入式汇编

```
asm( "pushl %eax\n\t"
     "movl $0,%eax\n\t"
     "popl %eax");
asm("movl %eax,%ebx");
asm("xorl %ebx,%edx");
asm("movl $0,_booga");
```