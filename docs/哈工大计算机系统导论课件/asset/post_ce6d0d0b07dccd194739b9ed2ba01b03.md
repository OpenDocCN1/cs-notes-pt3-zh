
## 计算序列: ret

|  | ret |  |
|---|---|---|
| 取指 | icode:ifun ← M₁[PC] | 读指令字节 |
| 译码 | valA ← R[%rsp] valB ← R[%rsp] | 读操作数栈指针 读操作数栈指针 |
| 执行 | valE ← valB + 8 | 栈指针增加 |
| 访存 | valM ← M₈[valA] | 读返回地址 |
| 写回 | R[%rsp] ← valE | 更新栈指针 |
| 更新PC | PC ← valM | PC指向返回地址 |

- 利用ALU增加栈指针的值
- 从内存中读取返回地址

## 计算序列

| | | OPq rA, rB |
|---|---|---|
| 取指 | icode,ifun | icode:ifun ← M1[PC] |
|  | rA,rB | rA:rB ← M1[PC+1] |
|  | valC |  |
|  | valP | valP ← PC+2 |
| 译码 | valA, srcA | valA ← R[rA] |
|  | valB, srcB | valB ← R[rB] |
| 执行 | valE | valE ← valB OP valA |
|  | Cond code | Set CC |
| 访存 | valM |  |
| 写回 | dstE | R[rB] ← valE |
|  | dstM |  |
| 更新PC | PC | PC ← valP |

读指令字节
读寄存器字节
[读常数字]
计算下一条PC
读操作数A
读操作数B
执行ALU的操作
设置条件码寄存器
[读写内存]
ALU的运算结果写回
[内存结果写回]
更新PC

- 所有的指令有相同的格式
- 每一步计算的内容有区别

## 计算序列

| | | call Dest |
|---|---|---|
| 取指 | icode,ifun | icode:ifun ← M1[PC] |
|  | rA,rB |  |
|  | valC | valC ← M8[PC+1] |
|  | valP | valP ← PC+9 |
| 译码 | valA, srcA | [读操作数A] |
|  | valB, srcB | valB ← R[%rsp] |
| 执行 | valE | valE ← valB + -8 |
|  | Cond code | [设置条件码寄存器] |
| 访问 | valM | M8[valE] ← valP |
| 写回 | dstE | R[%rsp] ← valE |
|  | dstM | [内存结果写回] |
| 更新PC | PC | PC ← valC |

读指令字节
[读寄存器字节]
读常数字
计算下一条PC
[读操作数A]
读操作数B
执行ALU的操作
[设置条件码寄存器]
内存读写
ALU的运算结果写回
[内存结果写回]
更新PC

- 所有指令遵循同样的一般格式
- 区别在于每一步计算的不同

## 计算的数值

- 取指
  - icode 指令码
  - ifun 指令功能
  - rA 指令寄存器A
  - rB 指令寄存器B
  - valC 指令中的常数
  - valP 增加PC
- 译码
  - srcA 寄存器ID A
  - srcB 寄存器ID B
  - dstE 目的寄存器E
  - dstM 目的寄存器M
  - valA 寄存器值A
  - valB 寄存器值B
- 执行
  - valE ALU运算结果
  - Cnd 分支或转移标识
- 访存
  - valM 内存中的数值

## SEQ 硬件结构

- 说明
  - 浅蓝色方框:
    硬件单元
    - 例如内存、ALU等等
  - 灰色方框:
    控制逻辑
    - 用HCL语言描述
  - 白色的椭圆框:
    信号标识
  - 粗线:
    宽度为字长的数据（64位）
  - 细线:
    宽度为字节或更窄的数据（4-8位）
  - 虚线:
    单个位的数据

![](img/7ab811dea080313a753fa0ae68528fa9_886_0.png)

## 取指逻辑

![](img/7ab811dea080313a753fa0ae68528fa9_887_0.png)

## 预定义的单元

- PC: 存储PC的寄存器
- 指令内存: 读十个字节 (PC to PC+9)
  - 发出指令地址不合法的信号
- Split: 把指令字节分为icode和ifun
- Align: 把读出的字节放入寄存器和常数字中

## 取指逻辑

![](img/7ab811dea080313a753fa0ae68528fa9_888_0.png)

## 控制逻辑

- Instr. Valid: 指令是否有效？
- icode, ifun: 指令地址无效时生成no-op指令
- Need regids: 指令是否有寄存器字节？
- Need valC: 指令是否有常数字？

## HCL描述的取指控制逻辑

```
# Determine instruction code
int icode = [
    imem_error: INOP;
    1: imem_icode;
];

# Determine instruction function
int ifun = [
    imem_error: FNONE;
    1: imem_ifun;
];
```

![](img/7ab811dea080313a753fa0ae68528fa9_889_0.png)

## HCL描述的取指控制逻辑

nop  0 0

halt  1 0

rrmovl rA, rB  2 0 rA rB

irmovl V, rB  3 0 8 rB  V

rmmovl rA, D(rB)  4 0 rA rB  D

mrmovl D(rB), rA  5 0 rA rB  D

OP1 rA, rB  6 fn rA rB

jXX Dest  7 fn  Dest

call Dest  8 0  Dest

ret  9 0

pushl rA  A 0 rA 8

popl rA  B 0 rA 8

need_regids

## HCL描述的取指控制逻辑

```
bool need_regids = icode in
{ IRRMOVQ, IOPQ, IPUSHQ, IPOPQ,
  IIRMOVQ, IRMMOVQ, IMRMOVQ };
```

```
bool instr_valid = icode in
{ INOP, IHALT, IRRMOVQ, IIRMOVQ,
  IRMMOVQ, IMRMOVQ, IOPQ, IJXX, ICALL,
  IRET, IPUSHQ, IPOPQ };
```

## 译码与写回逻辑

### 寄存器文件

- 读端口 A, B
- 写端口 E, M
- 地址为寄存器的ID 或 15 (0xF) (非法访问)

### 控制逻辑

- srcA, srcB: 读端口地址
- dstE, dstM: 写端口地址

### 信号

- Cnd: 标明是否触发条件转移
- 在执行阶段计算出Cnd条件信号

![](img/7ab811dea080313a753fa0ae68528fa9_892_0.png)

## srcA

|  | OPq rA, rB |  |
|译码| valA ← R[rA] | 读操作数A |
|  | cmovXX rA, rB |  |
|译码| valA ← R[rA] | 读操作数A |
|  | rmmovq rA, D(rB) |  |
|译码| valA ← R[rA] | 读操作数A |
|  | popq rA |  |
|译码| valA ← R[%rsp] | 读栈指针 |
|  | jXX Dest |  |
|译码|  | 无操作数 |
|  | call Dest |  |
|译码|  | 无操作数 |
|  | ret |  |
|译码| valA ← R[%rsp] | 读栈指针 |

```
int srcA = [
    icode in { IRRMOVQ, IRMMOVQ, IOPQ, IPUSHQ } : rA;
    icode in { IPOPQ, IRET } : RRSP;
    1 : RNONE; # 不需要寄存器
];
```

## dstE

| Instruction | Action | Description |
|-------------|--------|-------------|
| OPq rA, rB | 写回 R[rB] ← valE | 结果写回 |
| cmovXX rA, rB | 写回 R[rB] ← valE | 有条件的写回结果 |
| 写回 | R[rB] ← valE | 无 |
| xm movq rA, D(rB) | 写回 R[rB] ← valE | 无 |
| popq rA | 写回 R[%rsp] ← valE | 更新栈指针 |
| jXX Dest | 写回 | 无 |
| call Dest | 写回 R[%rsp] ← valE | 更新栈指针 |
| ret | 写回 R[%rsp] ← valE | 更新栈指针 |

```
int dstE = [
icode in { IRRMOVQ } && Cnd : rB;
icode in { IRRMOVQ, IOPQ } : rB;
icode in { IPUSHQ, IPOPQ, ICALL, IRET } : RRSP;
1 : RNONE; # 不写任何寄存器
```
