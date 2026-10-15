

## 整数寄存器
## 将现有寄存器扩展到 64 位

| %rax | %eax | %ah | %al |
| %rbx | %edx | %dh | %dl |
| %rcx | %ecx | %ch | %cl |
| %rdx | %ebx | %bh | %bl |
| %rsi | %esi |  |  |
| %rdi | %edi |  |  |
| %rsp | %esp |  |  |
| %rbp | %ebp |  |  |

## 整数寄存器
新增 8 个 64 位寄存器

| %rax | %eax | %ah | %al | %r8 | %r8d |
| %rbx | %ebx | %dh | %dl | %r9 | %r9d |
| %rcx | %ecx | %ch | %cl | %r10 | %r10d |
| %rdx | %edx | %bh | %bl | %r11 | %r11d |
| %rsi | %esi |  |  | %r12 | %r12d |
| %rdi | %edi |  |  | %r13 | %r13d |
| %rsp | %esp |  |  | %r14 | %r14d |
| %rbp | %ebp |  |  | %r15 | %r15d |

## 整数寄存器
## 使 %ebp/%rbp 成为通用用途

| %rax | %eax | %ah | %al |
| %rbx | %ebx | %dh | %dl |
| %rcx | %ecx | %ch | %cl |
| %rdx | %edx | %bh | %bl |
| %rsi | %esi |  |  |
| %rdi | %edi |  |  |
| %rsp | %esp |  |  |
| %rbp | %ebp |  |  |

| %r8 | %r8d |
| %r9 | %r9d |
| %r10 | %r10d |
| %r11 | %r11d |
| %r12 | %r12d |
| %r13 | %r13d |
| %r14 | %r14d |
| %r15 | %r15d |

## 指令

- 长字 l (4 字节) ↔ 四字 q (8 字节)

- 新指令
  - `movl` → `movq`
  - `addl` → `addq`
  - `sall` → `salq`
  - 等等。

- 32 位指令生成 32 位结果
  - 将目标寄存器的高位清零
  - 示例：`addl`

## Switch 语句
## 跳转表

```
long switch(long x)
{
    switch(x) {
        . . .
    }
    . . .
}
```

```
.section .rodata
.align 4
.L8:
    .long .L1 # x = 0
    .long .L2 # x = 1
    .long .L3 # x = 2
    .long .L4 # x = 3
    .long .L5 # x = 4
    .long .L6 # x = 5
    .long .L7 # x = 6
```

```
switch:
    pushl %ebp          # Setup
    movl %esp, %ebp     # Setup
    movl 8(%ebp), %edx  # edx = x
    cmpl $6, %edx       # x:6
    ja .L1              # if > goto default
    jmp *.L8(, %edx, 4) # goto JTab[x]
```

## Switch 语句

- x86-64
  - 相同的总体思路，适配到 64 位代码
  - 表项为 64 位（指针）

```
.section .rodata
    .align 4
.L8:
    .long .L1 # x = 0
    .long .L2 # x = 1
    .long .L3 # x = 2
    .long .L4 # x = 3
    .long .L5 # x = 4
    .long .L6 # x = 5
    .long .L7 # x = 6
```

IA32

```
.section .rodata
    .align 8
.L8:
    .quad .L1 # x = 0
    .quad .L2 # x = 1
    .quad .L3 # x = 2
    .quad .L4 # x = 3
    .quad .L5 # x = 4
    .quad .L6 # x = 5
    .quad .L7 # x = 6
```

x86-64

## 程序的机器级表示
(x86-64)

## 大纲

- x86-64 机器级编程
  - 过程与栈
  - 对齐
  - 字节序
- 建议阅读
  - 第 3.13 章

## 示例：swap()
## IA32

```
void
swap(int *xp, int *yp)
{
    int t0 = *xp;
    int t1 = *yp;
    *xp = t1;
    *yp = t0;
}
```

```
swap:
    pushl %ebp
    movl %esp,%ebp
    pushl %ebx
    movl 12(%ebp),%ecx
    movl 8(%ebp),%edx
    movl (%ecx),%eax
    movl (%edx),%ebx
    movl %eax,(%edx)
    movl %ebx,(%ecx)
    movl -4(%ebp),%ebx
    movl %ebp,%esp
    popl %ebp
    ret
```

设置

主体

结束

## 示例：swap()
## x86-64

```
void
swap(int *xp, int *yp)
{
    int t0 = *xp;
    int t1 = *yp;
    *xp = t1;
    *yp = t0;
}
```

```
swap:
movl (%rdi), %edx
movl (%rsi), %eax
movl %eax, (%rdi)
movl %edx, (%rsi)
retq
```

## 示例：swap()

操作数通过寄存器传递

- 第一个 (xp) 在 %rdi 中
- 第二个 (yp) 在 %rsi 中
- 64 位指针

```
swap:
movl (%rdi), %edx
movl (%rsi), %eax
movl %eax, (%rdi)
movl %edx, (%rsi)
retq
```

无需栈操作

32 位数据

- 数据保存在寄存器 %eax 和 %edx 中
- movl 操作

## 示例：swap()
## 交换 64 位中的长整型

```
void
swap(long int *xp,
    long int *yp)
{
    long int t0 = *xp;
    long int t1 = *yp;
    *xp = t1;
    *yp = t0;
}
```

```
swap:
movq (%rdi), %rdx
movq (%rsi), %rax
movq %rax, (%rdi)
movq %rdx, (%rsi)
retq
```

64 位数据

数据保存在寄存器 %rax 和 %rdx 中

movq 操作

"q" 代表四字

