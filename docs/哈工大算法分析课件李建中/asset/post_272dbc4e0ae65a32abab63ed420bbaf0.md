
## Accounting方法概述

- Accounting方法
- 直观地为每个操作分配摊销费用上界
- 一个操作实际费用与摊销费用
- 若摊销费用大于实际费用则多余部分作为信用
- 若实际费用大于摊销费用则用之前操作积累的信用
- 摊销费用中积累的Credit称为操作积累的预付款，即余额，记 Σi≤j αi - Σi≤j ci ≥0 永远为真
- 零摊销费用满足：
- 对于i, αi, ci 有操作i的实际费用ci和摊销费用αi
- Σi≤j αi ≥ Σi≤j ci 表明对于任意小操作序列都是真

## 栈操作序列分析

- 栈操作序列条件
- Cost(PUSH)=1
- Cost(POP)=1
- Cost(MULTIPOP)=min(k,s)
- 栈操作序列分析
- Cost(PUSH)=2
- 一个操作序列中PUSH操作上
- 一个入栈操作对应一个出栈操作上，其入栈POP操作
- Cost(POP)=0
- Cost(MULTIPOP)=0
- 零摊销费用是
- Σi≤j αi - Σi≤j ci ≥0 表明对于任意不相邻操作序列都是真
- n个操作序列的摊销是零摊销
- O(n)

## 二进制栈叠Increment操作序列分析

- Increment操作序列分析
- 每次一增量操作
- 从栈底至栈顶“1”上，计数子栈底至栈顶0的个数
- 若操作序列为“1”上，计数子栈底至栈顶0的个数
- 若操作序列为“0”上，计数子栈底至栈顶0的个数
- Cost(Inrement)=2
- 零摊销费用是
- Σi≤j αi ≥ Σi≤j ci 对于任意小操作序列都是真。例
- 每次操作时，付给操作实际Credit费用
- n个Increment操作序列是零摊销
- O(n)

## 7.4 The Potential Method

- Potential方法概述原理
- Potential方法实现例子一
- Potential方法实现例子二

## Potential方法概述

- Potential方法
- 直观地为每个操作序列分配摊销费用上界
- 每次操作费用，为操作实际费用和势能变化的和
- 每次操作费用为操作实际费用和势能变化的和
- Potential方法把操作序列的每个操作费用看成，其势能变化和实际费用之和，称为操作序列的摊销费用
- 每次操作费用大于实际费用时，多余部分作为信用
- 每次操作费用小于实际费用时，用之前操作积累的信用
- 每次操作费用大于实际费用时，多余部分作为信用
- 每次操作费用小于实际费用时，用之前操作积累的信用

## 数据结构势能定义

- 势能是初始数据结构D0,此数据结构不相邻
- 一个操作序列
- 每次操作费用ci
- 每次操作费用ci, 实际费用ci, 势能D_i
- 每次操作费用ci = ci + φ(D_i) - φ(D_{i-1})
- 每次操作费用ci = ci + φ(D_i) - φ(D_{i-1})
- n个操作序列不相邻操作 (每次操作费用序列上界)
Σ α_i = Σ (c_i + φ(D_i) - φ(D_{i-1}))
= Σ c_i + φ(D_n) - φ(D_0)
- 每次操作费用
- 每次操作费用ci, 实际费用ci, 势能D_i
- 每次操作费用ci, 实际费用ci, 势能D_i, 下一个操作费用D_{i+1}
- 要求不依赖于φ(D_i)=0, φ(D_i)≥0

## 栈操作序列的性质

- 栈操作序列定义
- φ(D_i)是栈中D_i中出现的最小下标, 记为
- φ(D_1)=0, D_i出现
- φ(D_i)=i-1, 每条操作序列中最小下标小于0
- n个操作序列中最小下标
- 栈操作序列性质 (假设D_i中第i个元素)
- PUSH: α_i=c, φ(D_i)=j, D_{i+1}=j+1, i≠2
- POP: α_i=c, φ(D_i)=j, D_{i+1}=j-1
- MULTIPOP(k): k: k'=min(k,i)
α_i=c, φ(D_i)=j, D_{i+1}=j-k', -k'=0
- n个操作序列中平均时间复杂度O(n)

## 二进制计数器操作序列的性质

- 计数器操作序列定义
- φ(D_i)交替, D_i为计数器操作序列中第i个操作b_i
- φ(D_0)=0, D_i出现
- φ(D_i)=φ(D_{i-1})+1, 每条操作序列中最小下标小于0
- n个操作序列中最小下标
- INCREMENT T INCREMENT 操作序列
- INCREMENT T INCREMENT resets(b_i), 变量b_i+1
- 计数器操作序列性质: φ(D_i)=φ(D_{i-1})+1
- If b_i=0, 则b_i resets b_i, 则b_{i-1}=b_{i-1}+1
- If b_i>0, 则b_{i-1}=b_{i-1}+1
- 对于b_i, b_{i+1}=b_i+1, b_{i+1}=b_i+1, b_{i+1}=b_i+1
φ(D_i)=φ(D_{i-1})+1, φ(D_{i+1})=φ(D_i)+1, i=2
- n个操作序列中平均时间复杂度O(n)

## 第七章

## Tree Searching Strategies

韩喜洲
计算科学与工程学院

## 概要

- 7.1 Motivation of Tree Searching
- 7.2 Basic Tree Searching Strategies
- 7.3 Optimal Tree Searching Strategies
- 7.4 Personnel Assignment Problem
- 7.5 Traveling Salesperson Optimization Problem
- 7.6 The A* Algorithm

## 参考资料

- 《计算机算法设计与分析》
- 第5章，第6章
- 《网站资料》
- 第七章

## 7.1 Motivation of Tree Searching

很多问题可表示成树。
子集、递归问题可使用树搜索策略解决

## 布尔表达式可满足性问题

- 问题的定义
- 输入：n个布尔变量 x1,x2,...,xn
是含 x1,x2,...,xn 的布尔表达式
- 输出：是否存在一个 x1,x2,...,xn 的赋值
使所给布尔表达式的值为真

- 把问题表示成树
- 一通过不断地做假设来构造搜索树
- （以最小变量 (x1,x2,x3) 为例）

![](img/9e822ee25d7fb44c33253ed3ff372fc1_76_0.png)

## 求解问题

- 一致等价系统：x_p x_p x_3 ∨ x_5, x_p ¬x_2

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_0.png)

## 8-Puzzle问题

- 问题定义
- 一般入：具有8个小方块的难题
- 一般出：移动到列，使这些移动，构成从初始到目标

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_1.png)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_2.png)

## 搜索与树搜索问题

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_3.png)

## Hamiltonian环问题

- 问题定义
- 一般入：具有n个节点的图G=(V,E)
- 一般出：G中是否存在Hamiltonian环

给定G的n条边遍历每个节点一次，形成的闭合环就是G的一个Hamiltonian环。

有Hamiltonian环：

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_4.png)

无Hamiltonian环：

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_5.png)

## 搜索与树搜索问题

![](img/9e822ee25d7fb44c33253ed3ff372fc1_77_6.png)
