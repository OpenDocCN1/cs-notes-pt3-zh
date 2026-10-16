# 第七章

# Tree Searching Strategies

韩喜洲
计算科学与工程学院

# 概要

+   7.1 Motivation of Tree Searching
+   7.2 Basic Tree Searching Strategies
+   7.3 Optimal Tree Searching Strategies
+   7.4 Personnel Assignment Problem
+   7.5 Traveling Salesperson Optimization Problem
+   7.6 The A* Algorithm

# 参考资料

+   《计算机算法设计与分析》
+     第5章，第6章
+   《网站资料》
+     第七章

# 7.1 Motivation of Tree Searching

很多问题可表示成树。
子集、递归问题可使用树搜索策略解决

# 布尔表达式可满足性问题

+   问题的定义
+     输入：n个布尔变量 x1,x2,...,xn
+          是含 x1,x2,...,xn 的布尔表达式
+     输出：是否存在一个 x1,x2,...,xn 的赋值
+          使所给布尔表达式的值为真

+   把问题表示成树
+     一通过不断地做假设来构造搜索树
+     （以最小变量 (x1,x2,x3) 为例）

![](bbox=[0.62, 0.8, 0.92, 0.95])