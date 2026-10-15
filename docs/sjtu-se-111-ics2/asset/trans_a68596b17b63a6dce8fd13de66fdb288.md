
![](img/9bd5f6161cb6607b56d2fb964d1b8794_128_0.png)

## SEQ CPU 实现

## 大纲

- SEQ 实现
- 推荐阅读 4.3.2, 4.3.4

## 我们今天要讨论什么？

- 顺序 CPU（SEQ）的实现
  - 每条指令在一个周期内完成。
  - 指令顺序执行。
  - 没有两条指令并行或重叠执行。

## SEQ 硬件结构

- 阶段
  - **取指**：从内存读取指令
  - **译码**：读取程序寄存器
  - **执行**：计算值或地址
  - **访存**：读取或写入数据
  - **写回**：写入程序寄存器
  - **PC**：更新程序计数器

PC

写回

访存

执行

译码

取指

![](img/9bd5f6161cb6607b56d2fb964d1b8794_133_0.png)

valM

数据存储器

addrs, data

a

valE

CC

ALU

aluA, aluB

valA, valB

srcA, srcB

dstE, dstM

A B F  
寄存器文件

valE, valM

icode:ifun,  
rA:rB

指令存储器

PC 增量

PC

newPC

## 语义与实现之间的区别

- ISA
  - 每个阶段都可能更新一些状态；这些更新按顺序发生。
- SEQ
  - 所有状态更新操作在时钟上升沿同时发生。

![](img/9bd5f6161cb6607b56d2fb964d1b8794_135_0.png)

## SEQ 硬件

- 蓝色方框：□ 重新设计的硬件模块
  - 例如，存储器、ALU
- 灰色方框：▭ 控制逻辑
  - 用 HCL 描述
- 白色椭圆：○ 信号标签
- 粗线：→ 32 位字值
- 细线：→ 4–8 位值
- 点线：.......→ 1 位值

## 取指逻辑

![](img/9bd5f6161cb6607b56d2fb964d1b8794_137_0.png)

## 取指逻辑

- 预定义模块
  - PC：包含 PC 的寄存器
  - 指令存储器：读取 6 个字节（PC 到 PC+5）
  - 拆分：将指令字节划分为 icode 和 ifun
  - 对齐：获取 rA、rB 和 valC 字段

![](img/9bd5f6161cb6607b56d2fb964d1b8794_138_0.png)

## 取指逻辑

![](img/9bd5f6161cb6607b56d2fb964d1b8794_139_0.png)

- **控制模块**
  - **指令有效：** 这条指令是否有效？
  - **需要 regids：** 这条指令是否有寄存器字节？
  - **需要 valC：** 这条指令是否有一个常数字？
  - **icode|ifun：** 如果 `imem_error`，则设为 “nop”

## 一些宏

| 名称 | 值 | 含义 |
|---|---|---|
| RESP | 6 | `%esp` 的寄存器 ID |
| RNONE | F | 表示不访问寄存器文件 |
| ALUADD | 0 | 加法操作的函数 |
| SAOK | 1 | 正常操作的状态码 |
| SADR | 2 | 地址异常的状态码 |
| SINS | 3 | 非法指令异常的状态码 |
| SHLT | 4 | `halt` 的状态码 |

| 指令 | 字节编码 | 操作数 |
|---|---|---|
| `nop` | `0 0` | |
| `halt` | `1 0` | |
| `rrmovl rA, rB` | `2 0` | `rA rB` |
| `irmovl V, rB` | `3 0 8 rB V` | |
| `rmmovl rA, D(rB)` | `4 0 rA rB D` | |
| `mrmovl D(rB), rA` | `5 0 rA rB D` | |
| `OP1 rA, rB` | `6 fn rA rB` | |
| `jXX Dest` | `7 fn Dest` | |
| `call Dest` | `8 0 Dest` | |
| `ret` | `9 0` | |
| `pushl rA` | `A 0 rA 8` | |
| `popl rA` | `B 0 rA 8` | |

`need_regids`

## 取指控制逻辑

```c
bool need_regids = icode in
{ IRRMOVL, IIRMOVL, IRMMOVL,
IMRMOVL, IOPL, IPUSHL, IPOPL };

bool instr_valid = icode in
{ INOP, IHALT, IRRMOVL, IIRMOVL,
IRMMOVL, IMRMOVL, IOPL, IJXX,
ICALL, IRET, IPUSHL, IPOPL };
```

## 译码与写回逻辑

![](img/9bd5f6161cb6607b56d2fb964d1b8794_144_0.png)

## 译码与写回逻辑

![](img/9bd5f6161cb6607b56d2fb964d1b8794_145_0.png)

- 预定义模块
  - 寄存器文件
    - 读端口 A、B 和写端口 E、M
    - 地址是寄存器 ID 或 F（无访问）

## 译码与写回逻辑

- 控制逻辑
  - srcA：valA 的读端口地址 `{rA, %esp}`
  - srcB：valB 的读端口地址 `{rB, %esp}`
  - dstE：valE 的写端口地址 `{rB, %esp}`
  - dstM：valM 的写端口地址 `{rA}`
  - Cnd：用于决定是否设置 valE（cmovXX）

![](img/9bd5f6161cb6607b56d2fb964d1b8794_146_0.png)

