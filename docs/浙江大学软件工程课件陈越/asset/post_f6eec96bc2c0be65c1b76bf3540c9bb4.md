

## § 4.程序复杂程度的定量度量

(5) 程序级别(program level): \( L = V^* / V \)
其中 potential volume \( V^* = (2+n_2^*) \log_2 (2+n_2^*) \)，\( n_2^* \) 为I/O变量的个数。这里 \( V^* \) 是 \( V \) 的最小值，2表示程序中至少有2个运算符 — 赋值符和调用符。
\( L \) 体现了抽象程度，编码语言越高级，\( L \) 越接近1。

(6) 工作量(effort): \( E = V / L \)。

(7) 潜在错误(potential error): \( B = N \log_2 n / 3000 \)。

注： It should be noted that Halstead's "laws" have generated substantial controversy and that not everyone agrees that the underlying theory is correct. However, experimental verification of Halstead's findings have been made for a number of programming languages.

## Project Part IV
## HDIS v1.0 的隆重推出

- 验收截止日期：11月28日 （星期二）
- 验收地点： 各组自定
- 验收内容：
  - ① 组长介绍分工情况及指定功能完成概况；
  - ② 个人工作介绍（编程人员演示模块功能；测试人员出示测试报告；文档人员出示相应文档、文件夹）。

注意：不到现场汇报工作者无成绩；交付验收日期拖延一日须扣1分。

- 作业：自习第六章 编程 (Coding)

## 第七章 测试 (Testing)

## 防不胜防的软件错误 ——

例1： 1963年，美国，飞往火星的火箭爆炸，损失$ 10 million.
原因：FORTRAN循环 DO 5 I = 1, 3 误写为 DO 5 I = 1.3

例2： 1996年，美国 Washington Post 报导
Dallas, Aug. 23 — The captain of an American Airlines jet that
crashed in Colombia last December entered an incorrect one-
letter computer command that sent the plane into a mountain,
the airline said today.

The crash killed **all but four of the 163 people aboard**.

American’s investigators concluded that the captain of the Boeing 757 apparently thought he had entered the coordinates for the intended destination, Cali.

But on most South American aeronautical charts, the one-letter code for Cali is the same as the one for Bogota, 132 miles in the opposite direction.

The coordinates for Bogota directed the plane toward the mountain, according to a letter by Cecil Ewell, American’s chief pilot and vice president for flight. The codes for Bogota and Cali are different in most computer databases, Ewell said.

例3：[摘自Pfleeger 书中的 “REAL-TIME EXAMPLE”]

Our real-time example is based on the embedded software in the Ariane-5, a space rocket belonging to the European Space Agency (ESA). On June 4, 1996, on its maiden flight, the Ariane-5 was launched and performed perfectly for approximately 40 seconds. Then, it began to veer off course. At the direction of an Ariane ground controller, the rocket was destroyed by remote control. The destruction of the uninsured rocket was a loss not only of the rocket itself, but also of the four satellites it contained; the total cost of the disaster was $500 million.

The business impact of the incident went well beyond the $500 million in equipment. In 1996, the Ariane-4 rocket and previous variants held more than half of the world’s launch contracts, ahead of American, Russian, and Chinese launchers. Thus, the credibility of the program was at stake, as well as the potential business from future Ariane rockets.

**Cause:** There was no discussion in the SRI (Inertial Reference System) **requirements documents** of the ways in which the Ariane-5 trajectory would be different from Ariane-4.

## § 1. 基本概念

1、定义： 测试是为了**发现程序中的错误**而执行程序的过程。

注意：① 只能尽可能查错，不能证明程序中 **没有错**；  
② 测试员与程序员不应是同一个人。

## 2、黑盒和白盒测试

- 黑盒测试(black-box , or closed-box testing):  
  Make sure that every kind of input is submitted,  
  and the output observed matches the output  
  expected. —— Functional testing

- **白盒测试**(white-box，or open-box, clear-box testing):  
  Use the structure of the program to test. —— Structural testing

**主要问题：** 穷尽测试(complete test)通常是不可能的。

例：(Black-box) 程序要求输入3个整形数据。若字长16位，则各种可能输入的排列组合共有

\[
2^{16}\times 2^{16}\times 2^{16}\approx 3\times 10^{14}\text{（种）}
\]

若程序执行需10^-3秒，则对于所有合法输入的测试大约需用一万年，而且还应测试输入非法数据的情况。

## § 1. 基本概念

例: (White-box) 下图所示的程序中共有 \( 5^{20} \approx 10^{14} \) 条可能的执行通路，显然，每条通路都执行一遍是不现实的。

![](img/caa6e55d367968a29a6a558fa69d0413_146_0.png)

## 3、测试步骤：

- (1) Component testing —— program design & coding bugs
- (2) Subsystem testing —— connections between modules
- (3) System testing —— requirements & system design
- (4) Acceptance testing —— customer joins in
- (5) Parallel running —— compare the new system with the old one.

# 测试阶段的信息流：

![](img/caa6e55d367968a29a6a558fa69d0413_147_0.png)

