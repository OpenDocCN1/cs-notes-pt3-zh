

## 第9章 代码优化

### 第4节 数据流分析

```
for each block B do {
    IN[B] = ∅;
    OUT[B] = GEN[B];
}
change = true;
while change do {
    change = false;
    for each block B do {
        IN[B] = ⋃_{P ∈ pred(B)} OUT[P];
        oldout = OUT[B];
        OUT[B] = IN[B] - KILL[B] ∪ GEN[B];
        if OUT[B] != oldout
            change = true;
    }
}
```

### 5. 活跃变量分析

- 在活跃变量分析中，我们希望知道对于变量 x 和点 p，x 在 p 处的值是否会沿着从 p 开始的流图中的某条路径被使用。
- 如果是，则称 x 在 p 处活跃；否则称 x 在 p 处死亡。

L.IN[B] = (L.OUT[B] - L.DEF[B]) ∪ L.USE[B]

L.OUT[B] = ⋃_{S ∈ succ(B)} L.IN[S]

succ(B) 是 B 的后继基本块的集合。

### 6. 活跃变量算法

- 输入。一个流图，其中每个基本块的 L.DEF 和 L.USE 均已计算。
- 输出。L.OUT[B]，即流图中每个基本块 B 出口处活跃的变量集合。
- 方法。

```
for each block B do {
    L.OUT[B] = ∅;
    L.IN[B] = L.USE[B];
}
change = true;
while change do {
    change = false;
    for each block B do {
        L.OUT[B] = ⋃_{S ∈ succ(B)} L.IN[S];
        oldin = L.IN[B];
        L.IN[B] = (L.OUT[B] - L.DEF[B]) ∪ L.USE[B];
        if L.IN[B] != oldin
            change = true;
    }
}
```

### 7. 定义-使用链

- 如果在语句 s 处可能需要变量的右值，则称该变量在 s 处被使用。
- du-链问题是要计算在点 p 处某个变量（例如 x）的使用点 s 的集合，使得从 p 到 s 存在一条不重新定义 x 的路径。

## 实验说明

### 任务

Lab1: 词法分析器编程
Lab2: 语法分析器编程

注意事项:
1. 编程语言不限（最好是 C 或 Java）。
2. 你可以采用建议的可选方法中的任意一种来完成实验。
3. 词法和语法定义的复杂度由你自己决定。

### Lab1 要求

1. 输入
   - 字符流
   - REs（数量由你自己决定）
2. 输出
   - 记号序列
3. 单词类别由你自己定义
4. 可包含错误处理

### Lab1 可选实现方法

1. 模拟 2.6.5 节中的程序
2. 基于 FA 编程
   - a. 自己定义一些 REs
   - b. 将 REs 转换为 NFAs
   - c. 将这些 NFAs 合并为单个 NFA
   - d. 将 NFA 转换为具有最少状态的 DFA
   - e. 基于 DFA 编程
3. 基于你自己的 Lex 生成程序
   - a. 设计你自己的 Lex
      - i. 定义 .l 文件
      - ii. 编程实现你自己的 Lex
   - b. 基于你自己的 Lex 生成程序

### Lab2 要求

1. 输入
   - 字符流
   - CFG（某些句子类别的 CFG 的组合）
2. 输出
   - 若使用自顶向下的语法分析方法，则为推导序列。
   - 若使用自底向上的语法分析方法，则为归约序列。
3. 句子类别由你自己定义
4. 可包含错误处理

### Lab2 可选实现方法

1. 递归下降分析
   - 非终结符与一个函数/子程序相对应
2. LL(1)
   - a. 基于 CFG 构造 LL(1) 分析表
   - b. 使用 LL(1) 分析表设计程序
3. LR(1)
   - a. 基于 CFG 构造 LR(1) 分析表
   - b. 使用 LR(1) 分析表设计程序

## 实验文档要求

1. 实验报告
   - a. 动机/目标
   - b. 内容描述
   - c. 思路/方法
   - d. 假设
   - e. 相关 FA 描述
   - f. 重要数据结构的描述
   - g. 核心算法的描述
   - h. 运行用例
   - i. 出现的问题及相关解决方案
   - j. 你的感想与评论
2. 实验光盘
   - a. 每个班需要为每个实验准备一张光盘
   - b. 每个人在光盘中对应一个目录
   - c. 在每个人的目录中，需要包含以下文件：
      - 输入文件
      - 输出文件
      - 源程序文件
      - 报告文件
      - 其他相关文件

