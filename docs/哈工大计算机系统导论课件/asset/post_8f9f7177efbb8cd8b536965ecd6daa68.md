
## 维护异常的顺序

![](img/7ab811dea080313a753fa0ae68528fa9_759_0.png)

- 为流水线寄存器增加状态字段
- 取指阶段设为 “AOK”，“ADR”（当取指地址错误），“HLT”（停机指令）或者 “INS”（非法指令）
- 解码和执行阶段传递值
- 访存阶段传递或设置为“ADR”
- 当指令进入写回阶段时，异常被触发

## 异常处理逻辑

### 取指阶段

```
# Determine status code for fetched instruction
int f_stat = [
    imem_error: SADR;
    !instr_valid : SINS;
    f_icode == IHALT : SHLT;
    1 : SAOK;
];
```

### 访存阶段

```
# Update the status
int m_stat = [
    dmem_error : SADR;
    1 : M_stat;
];
```

### 写回阶段

```
int Stat = [
    # SBUB in earlier stages indicates bubble
    W_stat == SBUB : SAOK;
    1 : W_stat;
];
```

![](img/7ab811dea080313a753fa0ae68528fa9_760_0.png)

## 流水线处理器中的副作用

```
# demo-exc3.ys
irmovq $100,%rax
rmmovq %rax,0x10000(%rax) # invalid address
addq %rax,%rax          # Sets condition codes
```

0x000: irmovq $100,%rax
0x00a: rmmovq %rax,0x10000(%rax)
0x014: addq %rax,%rax

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| F | D | E | M | W |
| F | D | E | M |  |
| F | D | E |  |  |

异常检测

条件码设置

### 期望的行为

- rmmovq 指令引起异常
- 其他指令不受影响

### 避免副作用

- 异常出现应该禁止状态更新
  - 非法指令转换为流水线气泡
    - 除非状态指示异常状态
  - 数据不会被写入无效的地址
  - 防止条件码进行无效更新
    - 在访存阶段检测异常
    - 在执行阶段禁止条件码更新
    - 必须在相同的时钟周期内发生
  - 在最后阶段处理异常
    - 当在访存阶段探测到异常时
      - 在下一个时钟周期将气泡插入访存阶段
    - 当在写回阶段探测到异常时
      - 停止异常指令
  - 包含在HCL代码中

## 状态变化的控制逻辑

设置条件码

```
# Should the condition codes be updated?
bool set_cc = E_icode == IOPQ &&
# State changes only during normal operation
!m_stat in { SADR, SINS, SHLT }
&& !W_stat in { SADR, SINS, SHLT };
```

阶段控制

也控制访存阶段的更新

```
# Start injecting bubbles as soon as exception passes through memory stage
bool M_bubble = m_stat in { SADR, SINS, SHLT }
|| W_stat in { SADR, SINS, SHLT };

# stall pipeline register W when exception encountered
bool W_stall = W_stat in { SADR, SINS, SHLT };
```

![](img/7ab811dea080313a753fa0ae68528fa9_763_0.png)

## 其他实际的异常处理

- 调用异常处理程序
  - 将PC入栈
    - PC指向故障指令或下一条指令
    - 通常和异常状态一起通过流水线传输
  - 跳转到处理程序的入口地址
    - 通常是固定地址
    - 被定义为ISA的一部分
- 实现
  - 尚未实现！ ---OS部分

## 性能评估

- 时钟频率
  - 以GHz计算
  - 阶段功能的划分和电路的设计
    - 保持每个阶段的工作量尽可能的小
- 指令的执行速率
  - CPI: 每指令周期数
  - 平均来说，每条指令需要的时钟周期数
  - 流水线功能设计和基准程序
    - 例如：分支预测错误的频率

## PIPE的CPI

- **CPI ≈ 1.0**
  - 每个周期取一条指令
  - 几乎每个周期都有有效的执行一条新指令
    - 虽然每个单独的指令具有5个周期的延迟
- **CPI > 1.0**
  - 有时必须停顿或取消分支
- **计算 CPI**
  - C：时钟周期
  - I：执行完成的指令数
  - B：插入的气泡个数 (C = I + B)
    CPI = C/I = (I+B)/I = 1.0 + B/I
  - 因子B/I代表因气泡而产生的平均处罚

## PIPE的CPI（续）

B/I = LP + MP + RP

### Typical Values

- LP:由加载/使用冒险停顿产生的处罚
  - 加载指令的比例 0.25
  - 加载指令需要停顿的比例 0.20
  - 每次插入气泡的数量 1
  - ⇒ LP = 0.25 * 0.20 * 1 = 0.05
- MP:由错误的分支预测产生的处罚
  - 条件转移指令的比例 0.20
  - 条件转移预测错误的比例 0.40
  - 每次插入气泡的数量 2
  - ⇒ MP = 0.20 * 0.40 * 2 = 0.16
- RP:由ret指令产生的处罚
  - 返回指令占的比例 0.02
  - 每次插入的气泡数量 3
  - ⇒ RP = 0.02 * 3 = 0.06

- 处罚造成的影响（三种处罚的总和）0.05 + 0.16 + 0.06 = 0.27
  ⇒ CPI = 1.27  (Not bad!)

## 取指逻辑回顾

- 在取指周期期间
  1. 选择PC
  2. 从指令存储器中读取指令
  3. 检查icode确定指令长度
  4. 递增PC
- 时间
  - 第二、四步需要大量时间

![](img/7ab811dea080313a753fa0ae68528fa9_769_0.png)

## 标准取指时序

![](img/7ab811dea080313a753fa0ae68528fa9_770_0.png)

- 确保每一部分都顺序执行
- 在确定PC增加多少之后才能计算PC的值

## 快速增加PC的电路

![](img/7ab811dea080313a753fa0ae68528fa9_771_0.png)

## 调整取指时间

![](img/7ab811dea080313a753fa0ae68528fa9_772_0.png)

- 64-Bit 增量
- 当PC被选择时立即执行
- 不必等到MUX再输出
- 和存储器读并行执行

## 更实际的取指逻辑

![](img/7ab811dea080313a753fa0ae68528fa9_773_0.png)

- 取指盒子
- 集成到指令缓存
- 取整个cache块 (16 or 32 bytes)
- 从当前块选择当前指令
- 提前获取下一个块
  - 当到达当前块的末尾
  - 或在分支目标处

## 现代 CPU 设计

### Instruction Control

Retirement Unit
Register File
Fetch Control
Address
Instruction Cache
Instructions
Instruction Decode
Operations
Register Updates
Prediction OK?

### Functional Units

Integer/Branch
General Integer
FP Add
FP Mult/Div
Load
Store
Operation Results
Addr.
Addr
Data
Data
Data Cache
Execution
