# 目标代码的反汇编

反汇编结果

```
0000000000400595 <sumstore>:
400595: 53              push    %rbx
400596: 48 89 d3          mov     %rdx,%rbx
400599: e8 f2 ff ff ff    callq  400590 <plus>
40059e: 48 89 03          mov     %rax,(%rbx)
4005a1: 5b              pop     %rbx
4005a2: c3              retq
```

# 反汇编器/反汇编程序(Disassembler)

```
objdump -d sum
```

+   - 检查目标代码的有用工具
+   - 分析指令的位模式
+   - 生成近似的汇编代码表述/译文
+   - 可处理a.out (完整可执行文件)或 .o 文件