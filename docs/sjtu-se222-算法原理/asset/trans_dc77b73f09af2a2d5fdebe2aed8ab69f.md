

## 我们在哪里？

- 最近点对
- 几何扫描
- 几何预备知识
- 一些基础几何算法
  - 凸包问题
  - 点集的直径
  - 线段相交

## 最大点问题

点 $p_2 = (x_2, y_2)$ **支配** 点 $p_1 = (x_1, y_1)$，记为 $p_1 \square p_2$，如果 $x_1 \le x_2$ 且 $y_1 \le y_2$。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_970_0.png)

点 $p$ 是 **最大点** 如果不存在点 $q$ 使得 $p \ne q$ 且 $p \square q$。

## 最大点问题

问题：MaximalPoints
输入：点集及其坐标 (x_i,y_i)。
输出：集合中的所有最大点。

事件

Θ(nlogn)

扫描线

![](img/a8f1b433a70f1e5c410c8b43e41b650e_971_0.png)

## 城市天际线

8
(1, 1)
(2, 2)
(3, 3)
(4, 2)
(5, 3)
(6, 2)
(7, 0)
(8, 1)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_973_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_973_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_973_2.png)

## 几何预备知识

- 点：p(x,y)
- 线段：((x1,y1),(x2,y2))
- **凸** 多边形：多边形 P 是 **凸** 的，如果 P 中任意两点连成的线段完全位于 P 内。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_975_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_975_1.png)

## 左转和右转

面积 = ?

D = | x₁ y₁ 1 |
      | x₂ y₂ 1 |
      | x₃ y₃ 1 |

D > 0

D < 0

![](img/a8f1b433a70f1e5c410c8b43e41b650e_976_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_976_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_976_2.png)

## 左转和右转

- 判断一个点是在线段下方还是上方。
- 判断两条线段是否相交。

## 我们在哪里？

- 最近点对
- 几何扫描
- 几何预备知识
- 一些基础几何算法
  - 凸包问题
  - 点集的直径
  - 线段相交

## 凸包

问题：ConvexHull
输入：平面上 n 个点的集合 S={p₁, p₂, ..., pₙ}，
输出：CH(S)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_979_0.png)

- Graham scan
- Jarvis’ march (gift-wrapping algorithm)
- Quick-hull

## Jarvis’ march

- 从某个 *极值点* 开始，该点保证在包上。
- 在每一步，测试每个点，并找到使 *右转最大* 的点。该点必须是包上的下一个点。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_980_0.png)

## Quick hull

- 给定凸包的弦 $p_i p_j$
- 找到离弦最远的点 $p_k$
- 三角形 $p_i p_j p_k$ 内部的点不可能在包上。将位于边 $p_i p_k$ 外部的点放入集合 s1，将位于边 $p_j p_k$ 外部的点放入集合 s2。
- 递归求解 s1 和 s2 的问题。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_981_0.png)

## Graham Scan

![](img/a8f1b433a70f1e5c410c8b43e41b650e_982_0.png)

Ronald Graham
(source from Wikipedia)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_982_1.png)

## Graham scan

![](img/a8f1b433a70f1e5c410c8b43e41b650e_983_0.png)

## 我们在哪里？

- 最近点对
- 几何扫描
- 几何预备知识
- 一些基础几何算法
  - 凸包问题
  - 点集的直径
  - 线段相交

## 点集的直径

![](img/a8f1b433a70f1e5c410c8b43e41b650e_987_0.png)

点集 *P* 的直径等于 *CH(P)* 的直径。

任何两点如果承认两条平行支撑线则称为 *antipodal pair*。

凸多边形中实现直径的任意一对顶点都是 *antipodal pair*。

如何找到 antipodal pairs？

