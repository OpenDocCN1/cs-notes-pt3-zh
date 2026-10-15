```
080483c4 <main>:
...
80483d5:  c7 04 24 38 85 04 08    movl    password ,(%esp)
80483dc:  e8 17 ff ff ff        call    80482f8 <printf@plt>
80483e1:  8d 45 f8              lea     0xfffffff8(%ebp),%eax
80483e4:  89 44 24 04           mov     %eax,0x4(%esp)
80483e8:  c7 04 24 48 85 04 08    movl    $0x8048548,(%esp)
80483ef:  e8 e4 fe ff ff        call    80482d8 <scanf@plt>
80483f4:  8b 45 f8              mov     0xfffffff8(%ebp),%eax
80483f7:  83 f8 7b              cmp     $0x7b,%eax
80483fa:  75 0e                 jne     804840a <main+0x46>
80483fc:  c7 04 24 4b 85 04 08    movl    survive ,(%esp)
8048403:  e8 c0 fe ff ff        call    80482c8 <puts@plt>
8048408:  eb 0c                 jmp     8048416 <main+0x52>
804840a:  c7 04 24 54 85 04 08    movl    bomb ,(%esp)
8048411:  e8 b2 fe ff ff        call    80482c8 <puts@plt>
8048416:  b8 00 00 00 00        mov     $0x0,%eax
...
8048423:  c3                   ret
```