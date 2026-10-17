# # Finding Jump Table in Binary

```
00000000004005e0 <switch_eg>:
4005e0:   48 89 d1    mov    %rdx,%rcx
4005e3:   48 83 ff 06   cmp    $0x6,%rdi
4005e7:   77 2b         ja     400614 <switch_eg+0x34>
4005e9:   ff 24 fd f0 07 40 00  jmpq   *0x4007f0(,%rdi,8)
4005f0:   48 89 f0        mov    %rsi,%rax
4005f3:   48 0f af c2     imul   %rdx,%rax
4005f7:   c3            retq
4005f8:   48 89 f0        mov    %rsi,%rax
4005fb:   48 99         cqto
4005fd:   48 f7 f9        idiv   %rcx
400600:   eb 05         jmp    400607 <switch_eg+0x27>
400602:   b8 01 00 00 00  mov    $0x1,%eax
400607:   48 01 c8        add    %rcx,%rax
40060a:   c3            retq
40060b:   b8 01 00 00 00  mov    $0x1,%eax
400610:   48 29 d0        sub    %rdx,%rax
400613:   c3            retq
400614:   b8 02 00 00 00  mov    $0x2,%eax
400619:   c3            retq
```