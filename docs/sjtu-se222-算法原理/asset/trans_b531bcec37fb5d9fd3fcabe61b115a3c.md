

# 我们在哪里？

- 最大流和最小割
- Ford-Fulkerson 方法
- 应用
  - 最大二分匹配
  - 边不相交路径
  - 顶点不相交路径
  - 网络连通性

# 应用：二分匹配

问题：MaxMatch
输入：一个无向图 G(V, E)
匹配是指一个子集 M ⊆ E，使得 M 中的任意两条边都没有公共顶点。
输出：寻找最大基数匹配

![](img/a8f1b433a70f1e5c410c8b43e41b650e_856_0.png)

# 应用：二分匹配

N 名学生申请 N 个工作。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_857_0.png)

每个人获得多个 offer。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_857_1.png)

有没有办法将所有学生匹配到工作？

![](img/a8f1b433a70f1e5c410c8b43e41b650e_857_2.png)

# 二分匹配问题

- 1 Alice
  - Adobe
  - Amazon
  - Google
- 2 Bob
  - Adobe
  - Amazon
- 3 Carol
  - Adobe
  - Facebook
  - Google
- 4 Dave
  - Amazon
  - Yahoo
- 5 Eliza
  - Amazon
  - Yahoo
- 6 Adobe
  - Alice
  - Bob
  - Carol
- 7 Amazon
  - Alice
  - Bob
  - Dave
  - Eliza
- 8 Facebook
  - Carol
- 9 Google
  - Alice
  - Carol
- 10 Yahoo
  - Dave
  - Eliza

# 应用：二分匹配

问题：BipartiteMatch
输入：一个二分图 G(V, E)
输出：G 中最大的匹配。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_858_0.png)

# 稳定匹配

一对未匹配的 m-w 是不稳定的，如果男人 m 和女人 w 更喜欢彼此而不是当前伴侣。
稳定匹配是没有不稳定对的完美匹配。

|  | 1st | 2nd | 3rd |
|---|---|---|---|
| Xavier | Amy | Bertha | Clare |
| Yancey | Bertha | Amy | Clare |
| Zeus | Amy | Bertha | Clare |

男性的偏好档案

|  | 1st | 2nd | 3rd |
|---|---|---|---|
| Amy | Yancey | Xavier | Zeus |
| Bertha | Xavier | Yancey | Zeus |
| Clare | Xavier | Yancey | Zeus |

女性的偏好档案

X-C, Y-B, Z-A      不稳定
X-A, Y-B, Z-C      稳定

# 应用：边不相交路径

问题：EdgeDisjointPath
输入：一个图 G(V, E)，和两个顶点 s,t
输出：s 和 t 之间边不相交路径的最大数量

![](img/a8f1b433a70f1e5c410c8b43e41b650e_860_0.png)

# 应用：顶点不相交路径

**问题：** VertexDisjointPath  
**输入：** 一个图 G(V, E)，和两个顶点 s,t  
**输出：** s 和 t 之间顶点不相交路径的最大数量

![](img/a8f1b433a70f1e5c410c8b43e41b650e_861_0.png)

# 应用：顶点不相交路径

问题：VertexDisjointPath
输入：一个图 G(V, E)，和两个顶点 s,t
输出：s 和 t 之间顶点不相交路径的最大数量

![](img/a8f1b433a70f1e5c410c8b43e41b650e_862_0.png)

# 应用：顶点不相交路径

问题：VertexDisjointPath
输入：一个图 G(V, E)，和两个顶点 s,t
输出：s 和 t 之间顶点不相交路径的最大数量

![](img/a8f1b433a70f1e5c410c8b43e41b650e_863_0.png)

归约为边不相交路径问题

# 应用：网络连通性

问题：NetworkConnectivity
输入：一个图 G(V, E)，和两个顶点 s,t
输出：使 t 与 s 断开所需移除的最少边数

![](img/a8f1b433a70f1e5c410c8b43e41b650e_864_0.png)

找到最小割

# 结论

- **最小割问题**。找到容量最小的 st-cut。
  **最大流问题**。找到值最大的 st-flow。
  **对偶性**。最大流的值 = 最小割的容量。
- 已证明的**成功方法**。
  **Ford-Fulkerson**（各种增广路径策略）。
  **Preflow-push**（各种版本）。
- 开放的研究挑战。
  **实践**：以线性时间求解实际最大流/最小割问题。
  **理论**：证明其对最坏情况输入成立。

# Lecture 12 **P 和 NP**

- 计算复杂性的介绍
- 类 P 和 NP
- 类 NPC（NP-完全）

# 路线图

- 计算复杂性的介绍
- 类 P 和 NP
- 类 NPC

# 计算问题

- 什么是通用计算机？
- 数字计算机的能力是否存在极限？

![](img/a8f1b433a70f1e5c410c8b43e41b650e_868_0.png)

