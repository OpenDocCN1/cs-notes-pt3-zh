

## 3.1 控制方式与时序系统

### 时序部件

![](img/bd869e76e3d6f47b5ddb2de136bf6ccf_337_0.png)

![](img/bd869e76e3d6f47b5ddb2de136bf6ccf_337_1.png)

## 3.2 指令流程与微操作时间表

指令周期分析（针对模型计算机及其指令系统而言）

- 取指周期的微操作流程
- MOV指令的微操作流程
- 单操作数指令的微操作流程
- 双操作数指令的微操作流程
- 其他指令的微操作流程

## 3.2 指令流程与微操作时间表

### 指令的执行过程

- 取指：从存取器读取当前指令送到指令寄存器（IR），要根据指令编码的长度才能确定读取指令的详细流程。
- 取数：计算操作数地址，读取操作数，要根据操作数的来源与寻址方式才能确定具体的操作过程。
- 执行：执行并送结果。

## 3.2 指令流程与微操作时间表

### 取指周期的微操作流程

- 取指流程需要4个节拍
  - 指令地址送MAR
  - 存储器读出指令
  - 指令送MDR，并调整PC
  - 指令送IR

每条指令执行过程的第一个机器周期M1都是取指周期（取到指令核心部分）

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M1.T1 | 指令地址送MAR ( MAR ← PC ) | IB ← PC | CPMAR |
| M1.T2 | Read Memory | AB ← MAR, RD |  |
| M1.T3 | 指令送MDR ( MDR ← 指令 ) | MDR ← DB | CPMDR |
|  | 调整PC ( PC ← PC + 2 ) | PC+△ | CPPC |
| M1.T4 | MDR（指令）送IR ( IR ← MDR ) | IB ← MDR | CPIR |

## 3.2 指令流程与微操作时间表

### MOV AX, BX 指令执行的微操作流程

- 指令长度：16位，一次可读取完毕（指令代码：89DBH）
- 读取指令周期：机器周期M1内完成
- 执行周期：机器周期M2内完成

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M1.T1 | 指令地址送MAR | IB ← PC | CPMAR |
| M1.T2 | Read Memory | RD |  |
| M1.T3 | 指令送MDR | MDR ← DB | CPMDR |
|  | 调整PC | PC+ △ | CPPC |
| M1.T4 | MDR（指令）送IR | IB ← MDR | CPIR |
| M2.T1 | BX送暂存器C | IB ← GR, RDGR | CPC, BX地址 |
| M2.T2 | 暂存器C送AX | IB ← C | CPGR, AX地址 |
| M2.T3 | 无操作 |  |  |
| M2.T4 | 无操作 |  |  |

## 3.2 指令流程与微操作时间表

### ◆ MOV AX，1000H[BX] 指令执行的微操作流程

- 指令长度：32位，分两次读取
- 读取指令周期：机器周期M1内完成（读第一个16位）
- 读变址值周期：机器周期M2内完成
- 取操作数周期：机器周期M3内完成
- 执行周期：机器周期M4内完成

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M1.T1 | 指令地址送MAR | IB ← PC | CPMAR |
| M1.T2 | Read Memory | RD |  |
| M1.T3 | 指令送MDR | MDR ← DB | CPMDR |
|  | 调整PC | PC+ △ | CPPC |
| M1.T4 | MDR（指令）送IR | IB ← MDR | CPIR |

![](img/bd869e76e3d6f47b5ddb2de136bf6ccf_343_0.png)

![](img/bd869e76e3d6f47b5ddb2de136bf6ccf_343_1.png)

## 3.2 指令流程与微操作时间表

### 结构图

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| 取地址值 |  |  |  |
| M2.T1 | PC送MAR | IB ← PC | CPMAR |
| M2.T2 | 从存储器读取1000H | RD |  |
| M2.T3 | 1000H送MDR | MDR ← DB | CPMDR |
|  | 调整PC | PC+ △ | CPPC |
| M2.T4 | MDR（即1000H）送D | IB ← MDR | CPD |
| 取数周期 |  |  |  |
| M3.T1 | 计算有效地址 (BX)+1000H 送 Z | IB ← GR, RDGR, ,A+B | BX地址, CPZ |
| M3.T2 | 源操作数地址 Z 送MAR | IB ← Z | CPMAR |
| M3.T3 | 读取源操作数 | RD |  |
| M3.T4 | 源操作数送MDR | MDR ← DB | CPMDR |

## 3.2 指令流程与微操作时间表

### MOV 1000H[BX], AX 指令执行的微操作流程

- 指令长度：32位，分两次读取（指令代码：89870010H）
- 读取指令周期：机器周期M1内完成（读第一个16位）
- 读变址值周期：机器周期M2内完成
- 取操作数周期：机器周期M3内完成

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M1.T1 | 指令地址送MAR | IB ← PC | CPMAR |
| M1.T2 | Read Memory | RD |  |
| M1.T3 | 指令送MDR | MDR ← DB | CPMDR |
|  | 调整PC | PC+ △ | CPPC |
| M1.T4 | MDR（指令）送IR | IB ← MDR | CPIR |

取指周期

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M2.T1 | PC送MAR | IB ← PC | CPMAR |
| M2.T2 | 从存储器读取1000H | RD |  |
| M2.T3 | 1000H送MDR | MDR ← DB | CPMDR |
|  | 调整PC | PC+△ | CPPC |
| M2.T4 | MDR（1000H）送D | IB ← MDR | CPD |
| M3.T1 | 计算有效地址（BX）+1000H 送Z | IB ← GR, RDGR, A+B | BX地址，CPZ |
| M3.T2 | 目的操作数地址送MAR | IB ← Z | CPMAR |
| M3.T3 | AX送MDR | IB ← GR, GRRD | AX地址，CPMDR |
| M3.T4 | 写存储器 | DB ← MDR；WR |  |

取变址值

执行周期

![](img/bd869e76e3d6f47b5ddb2de136bf6ccf_347_0.png)

## 3.2 指令流程与微操作时间表

### ADD 2000H[BX], 1000H 指令执行的微操作流程

- 指令长度：48位，分三次读取
- 读取指令周期：机器周期M1内完成（读第一个16位）
- 读变址值周期：机器周期M2内完成
- 取操作数周期：机器周期M3内完成
- 取立即数,完成加法：机器周期M4内完成
- 执行周期：机器周期M5内完成

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M1.T1 | 指令地址送MAR | IB ← PC | CPMAR |
| M1.T2 | Read Memory | RD |  |
| M1.T3 | 指令送MDR | MDR ← DB | CPMDR |
|  | 调整PC | PC+ △ | CPPC |
| M1.T4 | MDR（指令）送IR | IB ← MDR | CPIR |

取指令周期

| 时间节拍 | 完成功能 | 需要的微操作信号 | 需要的写入脉冲 |
|---|---|---|---|
| M2.T1 | PC送MAR | IB ← PC | CPMAR |
| M2.T2 | 从存储器读变址值2000H | RD | |
| M2.T3 | 2000H送MDR | MDR ← DB | CPMDR |
| M2.T3 | 调整PC | PC+△ | CPPC |
| M2.T3 | BX送暂存器D | IB ← GR, RDGR | CPD，BX地址 |
| M2.T4 | MDR（即2000H）送ALU，加法结果送Z | IB ← MDR, A+B | CPZ |
| M3.T1 | 目的操作数地址Z送MAR，地址暂存在C | IB ← Z | CPMAR, CPC |
| M3.T2 | 读取目的操作数 | RD | |
| M3.T3 | 目的操作数送MDR | MDR ← DB | CPMDR |
| M3.T4 | 目的操作数送D | IB ← MDR | CPD |

![](img/bd869e76e3d6f47b5ddb2de136bf6ccf_349_0.png)

