

## 限制：寄存器开销

- 随着尝试加深流水线，加载寄存器的开销变得更加显著
- 花在加载寄存器上的时钟周期百分比：
  - 1级流水线：6.25%
  - 3级流水线：16.67%
  - 6级流水线：28.57%
- 现代处理器设计通过非常深的流水线获得高速

## 数据依赖

![](img/9bd5f6161cb6607b56d2fb964d1b8794_182_0.png)

- 系统
  - 每个操作都依赖于前一个操作的结果

## 数据冒险

Comb. logic A

Reg

Comb. logic B

Reg

Comb. logic C

Reg

Clock

OP1

OP2

OP3

OP4

Time

![](img/9bd5f6161cb6607b56d2fb964d1b8794_183_0.png)

## 数据冒险

- 结果没有及时反馈以供下一个操作使用
- 流水线改变了系统的行为

```
1  irmovl $50, %eax
2  addl %eax, %ebx
3  mrmovl 100(%ebx), %edx
```

## SEQ+ CPU 实现

## 概要

- SEQ+ 实现
- 建议阅读 4.5.1

## SEQ 硬件 vs. SEQ+ 硬件

- SEQ 硬件
  - 阶段按顺序发生
  - 一次只有一个操作在进行
- SEQ+ 硬件
  - 仍是顺序实现
  - 将 PC 阶段重新排序至开头

## SEQ+ 硬件

- **PC 阶段**
  - 任务是为当前指令选择 PC
  - 基于前一条指令计算的结果
- **处理器状态**
  - PC 不再存储在寄存器中
  - 但可以根据其他存储的信息确定 PC

## PC 计算

```
int pc= [
    picode == ICALL : pValC;
    picode == IJXX && pBch : pValC;
    Picode == IRET : pValM;
    1 : pValP;
];
```

## 朴素流水线实现

## 概要

- 朴素 PIPE 实现
- 流水线冒险
- 建议阅读 4.5.2 ~ 4.5.5

![](img/9bd5f6161cb6607b56d2fb964d1b8794_193_0.png)

## 流水线阶段

- Fetch
  - 选择当前 PC
  - 读取指令
  - 计算递增的 PC
- Decode
  - 读取程序寄存器
- Execute
  - 操作 ALU
- Memory
  - 读或写数据内存
- Write Back
  - 更新寄存器文件

## PIPE- 硬件

- 流水线寄存器保存指令执行的中间值
- 正向（向上）路径
  - 值从一个阶段传递到下一个阶段
  - 不能跳过阶段
    - 例如，valC 经过解码

## 反馈路径

- 预测 PC
  - 猜测下一个 PC 的值
  - 分支信息
    - 跳转已取/未取
    - 穿透或目标地址
  - 返回点
    - 从内存读取
- 寄存器更新
  - 到寄存器文件写端口

![](img/9bd5f6161cb6607b56d2fb964d1b8794_198_0.png)

## Write back

## Memory

## Execute

## Decode

## Fetch

![](img/9bd5f6161cb6607b56d2fb964d1b8794_198_1.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_198_2.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_198_3.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_198_4.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_198_5.png)

| 阶段 | 流水线寄存器字段 |
|---|---|
| W | stat, icode, valE, valM, dstE, dstM |
| M | stat, icode, Cnd, valE, valA, dstE, dstM |
| E | stat, icode, ifun, valC, valA, valB, dstE, dstM, srcA, srcB |
| D | stat, icode, ifun, rA, rB, valC, valP |
| F | predPC |

## 预测 PC

- 在当前指令完成取指阶段后开始获取新指令
  - 没有足够的时间可靠地确定下一条指令
- 猜测将跟随的指令
  - 如果预测错误则恢复

## 我们的预测策略

- 不转移控制的指令
  - 预测下一个 PC 为 valP
  - 总是可靠的
- 调用和无条件跳转
  - 预测下一个 PC 为 valC（目标）
  - 总是可靠的

