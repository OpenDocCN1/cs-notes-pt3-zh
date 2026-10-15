

## 算术和逻辑运算

指令代码
功能代码

### Add

```
addl rA, rB 6 0 rA rB
```

### Subtract (rA from rB)

```
subl rA, rB 6 1 rA rB
```

### And

```
andl rA, rB 6 2 rA rB
```

### Exclusive-Or

```
xorl rA, rB 6 3 rA rB
```

- 统称为 "OP1"
- 编码仅由 "功能代码" 不同
  - 第一个指令字中的低 4 字节
- 作为副作用设置条件码
- 注意：没有乘法或除法运算

## Move Operations

`rrmovl rA, rB` — `2 0 rA rB` — Register --> Register

`irmovl V, rB` — `3 0 F rB V` — Immediate --> Register

`rmmovl rA, D(rB)` — `4 0 rA rB D` — Register --> Memory

`mrmovl D(rB), rA` — `5 0 rA rB D` — Memory --> Register

- 类似于 IA32 `movl` 指令
- 内存地址的格式更简单
- 使用不同名称以保持区分

## Move Instruction Examples

| IA32 | Y86 |
|---|---|
| movl $0xabcd, %edx | irmovl $0xabcd, %edx |
| movl %esp, %ebx | rrmovl %esp, %ebx |
| movl -12(%ebp),%ecx | mrmovl -12(%ebp),%ecx |
| movl %esp,0x12345(%edx) | rmmovl %esp,0x12345c(%edx) |

| movl $0xabcd, (%eax) | — |
| movl %eax, 12(%eax,%edx) | — |
| movl (%ebp,%eax,4),%ecx | — |

## Move Instruction Examples

| Y86 | Encoding |
|---|---|
| irmovl $0xabcd, %edx | 30 F2 cd ab 00 00 |
| rrmovl %esp, %ebx | 20 43 |
| mrmovl -12(%ebp),%ecx | 50 15 f4 ff ff ff |
| rmmovl %esp,0x12345(%edx) | 40 42 45 23 01 00 |

## Conditional Move Operations

```
cmovle rA, rB 2 1 rA rB
```

- 统称为 "cmovXX"

```
cmovl rA, rB 2 2 rA rB
```

- 共享相同的 "指令代码"

```
cmove rA, rB 2 3 rA rB
```

with rrmovl

```
cmovne rA, rB 2 4 rA rB
```

- 编码仅由 "功能代码" 不同

```
cmovge rA, rB 2 5 rA rB
```

```
cmovg rA, rB 2 6 rA rB
```

- 基于条件码的值
- 与 IA32 中的对应指令相同

## Y86 Program Stack

![](img/b3f8b91675c485f1e811aa092ebbf3d4_683_0.png)

- 存放程序数据的内存区域
- 用于 Y86 和 IA32 支持过程调用
- 栈顶由 %esp 指示
  - 栈顶元素的地址
- 栈向较低地址增长
  - 栈顶元素位于栈中的最低地址

## Stack Operations

```
pushl rA   a 0 rA F
```

- 将 %esp 减 4
- 将 rA 中的字存储到 %esp 指向的内存中
- 类似于 IA32 （pushl %esp → 保存旧的 %esp）

```
popl rA   b 0 rA F
```

- 从 %esp 指向的内存中读取字
- 保存到 rA 中
- 将 %esp 加 4
- 类似于 IA32 （popl %esp → movl (%esp) %esp）

## Subroutine Call and Return

![](img/b3f8b91675c485f1e811aa092ebbf3d4_685_0.png)

- 将下一条指令的地址压入栈
- 开始在 Dest 处执行指令
- 类似于 IA32

![](img/b3f8b91675c485f1e811aa092ebbf3d4_685_1.png)

- 从栈中弹出值
- 用作下一条指令的地址
- 类似于 IA32

## Miscellaneous Instructions

```
nop  0 0
```

- 什么都不做

```
halt  1 0
```

- 停止执行指令
- IA32 有可比的指令，但在用户模式下无法执行
- 我们将使用它来停止模拟器

## Y86 Assembly

```
IA32 code
Y86 code
int Sum(int *Start, int Count)
int Sum(int *Start, int Count)
1  Sum:
1  Sum:
2     pushl %ebp
2     pushl %ebp
3     movl %esp,%ebp
3     rrmovl %esp,%ebp
4     movl 8(%ebp),%ecx   ecx = Start   4     mrmovl 8(%ebp),%ecx
5     movl 12(%ebp),%edx  edx = Count 5     mrmovl 12(%ebp),%edx
6     xorl %eax,%eax      sum = 0      6     xorl %eax,%eax
7     testl %edx,%edx
7     andl %edx,%edx Set cc
8  je .L34
8  je End
```

## Y86 Instructions

IA32 code
Y86 code

```
9 .L35:
10   addl (%ecx),%eax   add *Start to sum
11   addl $4,%ecx        Start++
12   decl %edx           Count--
13   jnz .L35            Stop when 0
14 .L34:
15   movl %ebp,%esp
16   popl %ebp
•   ret

9 Loop:
10   mrmovl (%ecx),%esi
11   addl %esi,%eax
12   irmovl $4,%ebx
13   addl %ebx,%ecx
14   irmovl $-1,%ebx
15   addl %ebx,%edx
16   jne Loop
17 End:
18   rrmovl %ebp,%esp
19   popl %ebp
20   ret
```

