
## 旁白：蠕虫和病毒

- **蠕虫(Worm):程序**
  - 可以自行运行
  - 可以将自己的完整版本传播到其他计算机上
- **病毒(Virus): 代码**
  - 将自己添加到别的程序中
  - 不独立运行
- 两者通常都能在计算机之间传播并造成破坏。

## 针对缓冲区溢出攻击，怎么做？

- 避免溢出漏洞
- 使用系统级的防护
- 编译器使用“栈金丝雀”（stack canaries）

## 1. 代码中避免溢出漏洞(!)

```
/* Echo Line */
void echo() {
    char buf[4];   /* Way too small! */
    fgets(buf, 4, stdin);
    puts(buf);
}
```

例如，使用限制字符串长度的库例程

- fgets 代替 gets
- strncpy 代替 strcpy
- 在 scanf 函数中别用 %s
  - 用 fgets 读入字符串
  - 或用 %ns 代替 %s，其中 n 是一个合适的整数

## 2. 系统级防护

### 随机的栈偏移

- 程序启动后，在栈中分配随机数量的空间
- 将移动整个程序使用的栈空间地址
- 黑客很难预测插入代码的起始地址
- 例如：执行5次内存申请代码
  - 每次程序执行，栈都重新定位

![](img/7ab811dea080313a753fa0ae68528fa9_682_0.png)

## 3. 栈金丝雀(Stack Canaries)

- 想法
  - 在栈中buffer之后的位置放置特殊的值——金丝雀("canary")
  - 退出函数之前，检查是否被破坏
- 用GCC 实现
  - -fstack-protector
- 该选项现在是默认开启的(早期默认关闭)

```
unix> ./bufdemo-sp
Type a string: 0123456
0123456
```

```
unix> ./bufdemo-sp
Type a string: 01234567
*** stack smashing detected ***
```

## 保护缓冲区反汇编

echo:

```
40072f:  sub $0x18,%rsp
400733:  mov %fs:0x28,%rax
40073c:  mov %rax,0x8(%rsp)
400741:  xor %eax,%eax
400743:  mov %rsp,%rdi
400746:  callq 4006e0 <gets>
40074b:  mov %rsp,%rdi
40074e:  callq 400570 <puts@plt>
400753:  mov 0x8(%rsp),%rax
400758:  xor %fs:0x28,%rax
400761:  je 400768 <echo+0x39>
400763:  callq 400580 <__stack_chk_fail@plt>
400768:  add $0x18,%rsp
40076c:  retq
```

## 核对金丝雀

调用gets后

| call_echo 的栈帧 |
| 返回地址 (8 bytes) |
|  |
| 金丝雀 (8 bytes) |
| 00 36 35 34 |
| 33 32 31 30 |

```
/* Echo Line */
void echo(){
    char buf[4]; /* Way too small! */
    gets(buf);
    puts(buf);
}
```

```
echo:
    ...
    movq 8(%rsp), %rax    # Retrieve from stack
    xorq %fs:40, %rax     # Compare to canary
    je   .L6              # If same, OK
    call __stack_chk_fail # FAIL
.L6:
    ...
```

buf ← %rsp

Input: 0123456

## 面向返回的编程攻击（ROP，return oriented programming）

- **挑战(对黑客)**
  - 栈随机化使缓冲区位置难以预测。
  - 标记栈为不可执行，很难插入二进制代码
- **替代策略**
  - 使用已有代码
    - 例如：stdlib的库代码
  - 将片段串在一起以获得总体期望的结果。
  - 不用克服栈金丝雀
- **从小工具构建攻击程序**
  - 以ret结尾的指令序列
    - 单字节编码为0xc3
  - 每次运行，**代码的位置固定**
  - **代码可执行**

## 小工具例子 #1

```
long ab_plus_c(long a, long b, long c)
{
    return a*b + c;
}
```

```
00000000004004d0 <ab_plus_c>:
4004d0: 48 0f af fe      imul %rsi,%rdi
4004d4: 48 8d 04 17      lea (%rdi,%rdx,1),%rax
4004d8: c3              retq
```

rax ← rdi + rdx

小工具地址 = 0x4004d4

- 使用现有功能的尾部

## 小工具例子 #2

```
void setval(unsigned *p) {
    *p = 3347663060u;
}
```

```
<setval>:
4004d9: c7 07 d4 48 89 c7 movl $0xc78948d4,(%rdi)
4004df: c3 retq
```

movq %rax, %rdi的编码

rdi ← rax
小工具地址 = 0x4004dc

- 改变字节码的用途

## 面向返回编程(ROP)的执行

![](img/7ab811dea080313a753fa0ae68528fa9_691_0.png)

- **ret 指令触发**
  - 将开始运行 Gadget 1
- **每个小工具最终的 ret 将启动下一个小工具**
- **通过小工具序列的运行，达到攻击目的。**

## 主要内容

- 内存布局
- 缓冲区溢出
  - 安全隐患
  - 防护
- 浮点数

## 标量和SIMD操作

标量操作:单精度

```
addss %xmm0,%xmm1
```

![](img/7ab811dea080313a753fa0ae68528fa9_694_0.png)

SIMD 操作: 单精度

```
addps %xmm0,%xmm1
```

![](img/7ab811dea080313a753fa0ae68528fa9_694_1.png)

标量操作:双精度

```
addsd %xmm0,%xmm1
```

![](img/7ab811dea080313a753fa0ae68528fa9_694_2.png)

## 浮点基础

- 参数传递使用： %xmm0, %xmm1, ...
- 返回结果保存： %xmm0
- 所有XMM 寄存器都是调用者保存

```
float fadd(float x, float y)
{
    return x + y;
}
```

```
double dadd(double x, double y)
{
    return x + y;
}
```

```
# x in %xmm0, y in %xmm1
addss  %xmm1, %xmm0
ret
```

```
# x in %xmm0, y in %xmm1
addsd  %xmm1, %xmm0
ret
```

## 浮点数的内存引用

- 单数传递：整数型(包括指针)参数用通用寄存器
- 单数传递：浮点型参数用XMM 寄存器
- 使用不同的mov指令在XMM 寄存器之间、或者内存和 XMM 寄存器之间传送数值

```
double dincr(double *p, double v){
    double x = *p;
    *p = x + v;
    return x;
}
```

```
# p in %rdi, v in %xmm0
movapd  %xmm0, %xmm1  # Copy v
movsd   (%rdi), %xmm0 # x = *p
addsd   %xmm0, %xmm1  # t = x + v
movsd   %xmm1, (%rdi) # *p = t
ret
```
