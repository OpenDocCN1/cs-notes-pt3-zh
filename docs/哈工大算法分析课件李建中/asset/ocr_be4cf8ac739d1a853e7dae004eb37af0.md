# 第九章
Approximation Algorithm
陈青叶
计算科学与工程学院

# 目录
9.1 Introduction
9.2 The Vertex-cover Problem
9.3 The Traveling-salesman Problem
9.4 The Set-covering Problem
9.5 Randomization and Linear Programming
9.6 The Subset-sum Problem
9.7 Linear programming methods in approximate algorithms

# 参考资料
《Introduction to Algorithms》
• 第35章
《网络流》
• 第9章

# 9.1 Introduction
• 近似算法的基本概念
• 近似算法的性能分析

# 近似算法的基本概念
• 近似算法的应用背景
  - 很多实际问题属于NP-完全问题
  - NP-完全问题是很难找到多项式时间算法
  - 而解NP-完全问题算法：
    * 问题规模输入很小，可采用有最优解的算法直接解问题
    * 问题规模很大时，可采用近似算法
    * 许多问题与其它问题联系可采用近似解
• 什么叫近似算法
  - 能够找到一个优化问题的近似优化解的算法
  - 近似算法主要解决何问题

# 近似算法的性能分析
• 近似算法的性能度量
  - 一个算法解多项式时间可解最优解问题
• 近似算法的性能度量
  - 寻找解问题的近似解问题
  - 问题规模很大时，可采用近似算法
  - 我们的算法与最优解的比值
  - 一般算法多项式时间近似算法的性能比是性能比是
    * Ratio Bound
    * 相对误差
    * (1+ε)-近似