
## 欢迎来到 ICS(2)

## 大纲
- 教学人员
- 评分

## 授课教师

![](img/9bd5f6161cb6607b56d2fb964d1b8794_2_0.png)

藏越宇

邮箱：byzang@fudan.edu.cn

办公电话：13917124245

![](img/9bd5f6161cb6607b56d2fb964d1b8794_2_1.png)

陈榕

邮箱：rongchen@sjtu.edu.cn

办公电话：13616861826

## 助教

感谢 侯君

刘宇宸（LYC）

邮箱：[liuyuchen@sjtu.edu.cn](mailto:liuyuchen@sjtu.edu.cn)

闵师达（MSD）

邮箱：[minshistar@163.com](mailto:minshistar@163.com)

成立（CL）

邮箱：[lewischenq0204@gmail.com](mailto:lewischenq0204@gmail.com)

曾福山（ZFS）

邮箱：[chafee.hello@gmail.com](mailto:chafee.hello@gmail.com)

## 评分
- 考试（60%）
  - 期中考试（20%）
  - 期末考试（40%）
  - 所有考试均为开卷/开笔记。
- 实验（35%）
  - 4 次实验（每次占 7–10%）
- 作业（5%）

## 处理器架构

## 主题
- 回顾 y86 指令集架构
- 逻辑设计
- 硬件控制语言 HCL
- 建议阅读：4.1, 4.2

## 目标
- 理解计算机的基本组成
  - 指令集架构
- 深入探索 CPU 工作机制
  - 指令是如何执行的
- 帮助你编程
  - 充分理解计算机的组织和工作方式将帮助你编写更稳定、更高效的代码

## 指令集架构 #1
- 它是什么？
  - 汇编语言抽象
  - 机器语言抽象

指令集架构（ISA）
- 它提供了什么？
  - 真实计算机的一种抽象，隐藏实现细节
    - 计算机指令的语法
    - 指令的语义
    - 执行模型
    - 程序员可见的计算机状态

## 指令集架构 #2
- 汇编语言视角
  - 处理器状态
    - 寄存器、内存等
  - 指令
    - `addl, movl, leal, ...`
    - 指令如何编码为字节
- 抽象层
  - 上层：如何编程机器
    - 处理器按顺序执行指令
  - 下层：需要构建什么
    - 使用技巧使其运行更快
    - 例如，同时执行多条指令

![](img/9bd5f6161cb6607b56d2fb964d1b8794_10_0.png)

## 指令集架构 #3
- ISA 定义处理器家族
  - 两大类：RISC 和 CISC
    - RISC: SPARC, MIPS, PowerPC, ARM
    - CISC: X86（或称为 IA32）
- 在相同的 ISA 下，有许多不同的处理器
  - 来自不同的制造商
    - X86 来自 Intel、AMD 和 VIA
  - 不同的型号
    - 8086, 80386, Pentium, Pentium 4

## Y86 处理器状态
- 程序寄存器
  - 与 IA32 相同的 8 个寄存器，每个 32 位
- 条件码
  - 由算术或逻辑指令设置的单比特标志
    - OF：溢出  ZF：零  SF：负数
- 程序计数器
  - 指示指令的地址
- 内存
  - 字节可寻址的存储数组
  - 字以小端字节序存储

![](img/9bd5f6161cb6607b56d2fb964d1b8794_12_0.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_12_1.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_12_2.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_12_3.png)

## Y86 指令
- 格式（P259）
  - 从内存读取 1--6 字节的信息
    - 可以从第 1 个字节确定指令长度
    - 指令类型不如 IA32 多，编码也比 IA32 简单
  - 每条指令都会访问和修改程序状态的某些部分

| 长度 |  | 字节0 | 字节1 | 字节2 | 字节3 | 字节4 | 字节5 |
|---|---|---|---|---|---|---|---|
| 1 | nop | 0 | 0 |  |  |  |  |
| 1 | halt | 1 | 0 |  |  |  |  |
| 2 | rrmovl rA,rB | 2 | 0 | rA rB |  |  |  |
| 6 | irmovl V,rB | 3 | 0 | rA rB | V |  |  |
| 6 | rmmovl rA,D(rB) | 4 | 0 | rA rB | Dest |  |  |
| 6 | mrmovl D(rB),rA | 5 | 0 | rA rB | Dest |  |  |
| 2 | opl rA,rB | 6 | fn | rA rB |  |  |  |
| 2 | addl rA,rB | 6 | 0 | rA rB |  |  |  |
| 2 | subl rA,rB | 6 | 1 | rA rB |  |  |  |
| 2 | andl rA,rB | 6 | 2 | rA rB |  |  |  |
| 2 | xorl rA,rB | 6 | 3 | rA rB |  |  |  |
| 5 | jxx Dest | 7 | fn | Dest |  |  |  |
| 5 | jmp Dest | 7 | 0 | Dest |  |  |  |
| 5 | jle Dest | 7 | 1 | Dest |  |  |  |
| 5 | jl Dest | 7 | 2 | Dest |  |  |  |
| 5 | je Dest | 7 | 3 | Dest |  |  |  |
| 5 | jne Dest | 7 | 4 | Dest |  |  |  |
| 5 | jge Dest | 7 | 5 | Dest |  |  |  |
| 5 | jg Dest | 7 | 6 | Dest |  |  |  |
| 5 | call Dest | 8 | 0 | Dest |  |  |  |
| 1 | ret | 9 | 0 |  |  |  |  |
| 2 | pushl rA | A | 0 | rA 8 |  |  |  |
| 2 | popl rA | B | 0 | rA 8 |  |  |  |

## Y86 指令集

