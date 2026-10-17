# 3.5 LR分析器

从文法构造的识别活前缀的DFA的一些特点

**概念：有效项目**
如果 $S\Rightarrow_{rm} \alpha Aw\Rightarrow_{rm} \alpha\beta_1\beta_2w$，那么我们说项目 $A\to\beta_1\cdot\beta_2$ 对话前缀 $\alpha\beta_1$ 是有效的。

+   - 一个项目可能对好几个活前缀都是有效的。
+   - 一个活前缀可能有多个有效项目。
+   - 一个活前缀的有效项目集就是从这个DFA的初态出发，沿着标记为该活前缀的路径到达的那个项目集（状态）。