# 转发优先级

```
# demo-priority.ys
0x000: irmovq $1, %rax
0x00a: irmovq $2, %rax
0x014: irmovq $3, %rax
0x01e: rrmovq %rax, %rdx
0x020: halt
```

# 多重转发选择

+   - 哪一个应该具有最高优先级
+   - 匹配串行语义
+   - 使用从最早的流水线阶段获取的匹配值

![](bbox=[0.42, 0.19, 0.88, 0.92])