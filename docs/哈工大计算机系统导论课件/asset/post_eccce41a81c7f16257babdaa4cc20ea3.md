
# 转发的限制

```
# demo-luh.ys
0x000: irmovq $128,%rdx
0x00a: irmovq $3,%rcx
0x014: rmmovq %rcx, 0(%rdx)
0x01e: irmovq $10,%rbx
0x028: mrmovq 0(%rdx),%rax # Load %rax
0x032: addq %rbx,%rax # Use %rax
0x034: halt
```

- 加载-使用 依赖
  - 在周期7译码阶段结束时需要的值
  - 在周期8访存阶段才读取该值

![](img/7ab811dea080313a753fa0ae68528fa9_731_0.png)

# 检测 加载/使用 冒险

![](img/7ab811dea080313a753fa0ae68528fa9_733_0.png)

| 条件 | 触发 |
| --- | --- |
| 加载/使用 冒险 | E_icode in { IMRMOVQ, IPOPQ } && E_dstM in { d_srcA, d_srcB } |

# 加载/使用 冒险的控制

```
# demo-luh.ys
```

```
0x000: irmovq $128,%rdx
0x00a: irmovq $3,%rcx
0x014: rmmovq %rcx, 0(%rdx)
0x01e: irmovq $10,%rbx
0x028: mrmovq 0(%rdx),%rax # Load %rax
bubble
0x032: addq %rbx,%rax # Use %rax
0x034: halt
```

- 将指令暂停在取指和译码阶段
- 在执行阶段注入气泡

| 条件 | F | D | E | M | W |
|---|---|---|---|---|---|
| 加载/使用 冒险 | 暂停 | 暂停 | 气泡 | 正常 | 正常 |

![](img/7ab811dea080313a753fa0ae68528fa9_734_0.png)

# 分支预测错误示例

demo-j.ys

```
0x000:    xorq %rax,%rax
0x002:    jne t            # Not taken
0x00b:    irmovq $1, %rax   # Fall through
0x015:    nop
0x016:    nop
0x017:    nop
0x018:    halt
0x019: t: irmovq $3, %rdx   # Target
0x023:    irmovq $4, %rcx   # Should not execute
0x02d:    irmovq $5, %rdx   # Should not execute
```

- 只能执行最早的8条指令

# 处理预测错误

```asm
#demo-j.ys

0x000: xorq %rax, %rax
0x002: jne target #Not Taken
0x016: irmovq $2, %rdx #target
       bubble
0x020: irmovq $3, %rbx # target+1
       bubble
0x00b: irmovq $1, %rax # Fall through
0x015: halt
```
```

![](img/7ab811dea080313a753fa0ae68528fa9_736_0.png)

# 作为预测分支

- 取出 2 条目标指令

当预测错误时取消

- **在执行阶段检测到未选择该分支**
- 在紧跟的指令周期中，将处于执行和译码阶段的指令用气泡替换掉
- **此时没有出现副作用**

# 检测分支预测错误

![](img/7ab811dea080313a753fa0ae68528fa9_737_0.png)

| 条件 | 触发 |
| --- | --- |
| 分支预测错误 | E_icode = IJXX & !e_Cnd |

# 预测错误的控制

```
#demo-j.ys

0x000: xorq %rax, %rax
0x002: jne target #Not Taken
0x016: irmovq $2, %rdx #target
bubble
0x020: irmovq $3, %rbx # target+1
bubble
0x00b: irmovq $1, %rax # Fall through
0x015: halt
```

![](img/7ab811dea080313a753fa0ae68528fa9_738_0.png)

| 条件 | F | D | E | M | W |
| --- | --- | --- | --- | --- | --- |
| 分支预测错误 | 正常 | 气泡 | 气泡 | 正常 | 正常 |

# Return示例

demo-retb.ys

```
0x000:     irmovq Stack,%rsp   # Initialize stack pointer
0x00a:     call p             # Procedure call
0x013:     irmovq $5,%rsi     # Return point
0x01d:     halt
0x020: .pos 0x20
0x020: p: irmovq $-1,%rdi     # procedure
0x02a:     ret
0x02b:     irmovq $1,%rax     # Should not be executed
0x035:     irmovq $2,%rcx     # Should not be executed
0x03f:     irmovq $3,%rdx     # Should not be executed
0x049:     irmovq $4,%rbx     # Should not be executed
0x100: .pos 0x100
0x100: Stack:                 # Stack: Stack pointer
```

- 之前执行了3条额外的指令

# 正确的Return示例

```
#demo_retb
1: 0x026: ret
2: bubble
3: bubble
4: bubble
5: 0x013: irmovq $5, %rsi #return
```

- 当ret经过流水线时，暂停在取指阶段
  - 当处于译码、执行和访存阶段
- 在译码阶段注入气泡
- 当到达写回阶段释放暂停

![](img/7ab811dea080313a753fa0ae68528fa9_740_0.png)

# 检测Return

![](img/7ab811dea080313a753fa0ae68528fa9_741_0.png)

| 条件 | 触发 |
| --- | --- |
| 处理 ret | IRET in { D_icode, E_icode, M_icode } |

# Return的控制

```
# demoretb

0x026:     ret
    bubble
    bubble
    bubble

0x014: irmovq $5, %rsi # Return
```

![](img/7ab811dea080313a753fa0ae68528fa9_742_0.png)

| 条件 | F | D | E | M | W |
|---|---|---|---|---|---|
| 处理 ret | 暂停 | 气泡 | 正常 | 正常 | 正常 |

# 特殊控制情况

检测

| 条件 | 触发 |
| --- | --- |
| 处理 ret | IRET in { D_icode, E_icode, M_icode } |
| 加载/使用 冒险 | E_icode in { IMRMOVQ, IPOPQ } && E_dstM in { d_srcA, d_srcB } |
| 分支预测错误 | E_icode = IJXX & !e_Cnd |

动作(在下一个周期)

| 条件 | F | D | E | M | W |
| --- | --- | --- | --- | --- | --- |
| 处理 ret | 暂停 | 气泡 | 正常 | 正常 | 正常 |
| 加载/使用 冒险 | 暂停 | 暂停 | 气泡 | 正常 | 正常 |
| 分支预测错误 | 正常 | 气泡 | 气泡 | 正常 | 正常 |

# 实现流水线控制

![](img/7ab811dea080313a753fa0ae68528fa9_744_0.png)

- 组合逻辑产生流水线控制信号
- 动作发生在每个追随周期开始的时候
