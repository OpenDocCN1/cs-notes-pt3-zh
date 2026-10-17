

最近邻域法所求为：(a, c, e, d, b, a)  
总长为 7 + 6 + 8 + 5 + 14 = 40  
最短回路：(a, c, e, b, d, a)  
总长为 7 + 6 + 9 + 5 + 10 = 37。

## Graphs/图论

设 \( G = (V, E, W) \) 是 \( n \) 个顶点的完全无向图，满足三角不等式 \( w(i, j) + w(j, k) \geq w(i, k) \)，\( d_0 \) 是最短 \( H \) 回路 \( D_0 \) 的长度，\( d \) 是最近邻域法得到的 \( H \) 回路 \( D \) 的长度，则：

\[
\frac{d}{d_0} \leq \frac{1}{2}[\log_2 n] + \frac{1}{2}
\]

## 练习

pp.499  17, 26

## 7.1 图的概念/Introduction of Graph

## 7.2 图的术语/Graph Terminology

## 7.3 图的表示与同构/ Representing Graph and Graph Isomorphism

## 7.4 连通性/Connectivity

## 7.5 欧拉道路与哈密尔顿道路/ Euler and Hamilton Paths

## 7.6 最短道路问题/Shortest Path Problem

## 7.7 平面图/Planar Graphs

## 7.8 图的着色/Graph Coloring

## § 6 平面图/Planar Graphs

[定义]平面图：  
图 \( G = (V, E) \)，如果 \( E \) 中边除了在 \( V \) 中顶点处可以相交，在其他地方都可以不相交，则 \( G \) 称为平面图/Planar。  
其画法称为图的平面表示/Planar Representation。

下面的图 A、图 B 看上去有边相交的，但改画一下得 A′、B′，就知是平面图。但对 C、D 两图，无论如何改画，也无法使所有的边不相交。

A  
A′

Graphs/图论

Graphs/图论

Graphs / 图论

D (k₅)  
图 D 是 5 个顶点的完全图。  
非平面图。

## [定义]区域/region

被平面图中回路分割成互不重叠的连通块，这些块称为**区域/Region**。

(1) 如果不存在回路，整个平面只有一个区域。如图，分为四个区域。

(2) 有限区域与无限区域：区域内任两点距离有上界，称此区域为有限区域，否则为无限区域。上图中，区域 4 是无限区域。

## [定理1]（欧拉公式/Euler’s formula）

对任何一个连通平面简单图，有 \( v - e + \gamma = 2 \)，其中 \( v \) 为顶点数，\( e \) 为边数，\( \gamma \) 是区域数。

证明：  
对 \( e \) 归纳：  
(1) \( e = 1 \)，只有二种情况  
a) ______，\( v = 2 \)，\( \gamma = 1 \)，  
\( v - e + \gamma = 2 - 1 + 1 = 2 \)

b) ______，\( v = 1 \)，\( \gamma = 2 \)，  
\( v - e + \gamma = 1 - 1 + 2 = 2 \)

(2) 若 \( e = n - 1 \) 时欧拉公式成立  

\( e = n \) 时，  

a) 若 \( G \) 中有有限区域，去掉此区域的一条边，成 \( G' \)，只有 \( n - 1 \) 条边，满足 \( v' - e' + \gamma' = 2 \)，而 \( v = v' \)，\( e = e' + 1 \)，\( \gamma = \gamma' + 1 \)，仍有 \( v - e + \gamma = v' - e' - 1 + \gamma' + 1 = v' - e' + \gamma' = 2 \)。

b) 若 \( G \) 不存在有限区域，即 \( G \) 中无回路，必有次为 1 的顶点，去掉这个顶点及关联的边，得 \( G' \)，顶点和边都减少 1，区域数总为 1，由假设 \( G' \) 中只有 \( n - 1 \) 条边，满足 \( v' - e' + \gamma' = 2 \)，而 \( v = v' + 1 \)，\( e = e' + 1 \)，\( \gamma = \gamma' = 1 \)，\( v - e + \gamma = v' + 1 - e' - 1 + \gamma' = v' - e' + \gamma' = 2 \)。

由于平面图的区域比较难数（如果已能画成边不相交的图，则已明确是平面图了），对一些特殊的图，欧拉公式有以下推论。

### 【推论一】：

如果 \( G = (V, E) \) 是连通的平面简单图且 \( v \) 大于等于 3，则有 \( e \leq 3v - 6 \)。

问题：如何判定一个图是否为平面图？

[定义]同胚（次 2 范围内的同构）：增加或减少次为 2 的顶点，能使两个图同构，称为同胚/homeomorphic。

## 定理2 库氏定理/Kuratowski’s theorem

平面图判断的充要条件。

一个图是平面图的充分必要条件是它不含有与 \( K_5 \) 和 \( K_{3,3} \) 同胚的子图。

例：6 个顶点的完全图必不是平面图。

图 b 是图 a 的子图，图 b 去掉次为 2 的顶点 \( V_6 \)，使 \( V_1 \) 与 \( V_5 \) 直接相邻，就是 5 个顶点的完全图 \( K_5 \)，图 b 与 \( K_5 \) 同胚，所以图 a 一定不是平面图。当然，\( K_5 \) 也是图 a 的子图。

尽管有了库氏定理，判别一个图是否平面图还是相当困难。

Graphs/图论

Graphs/图论

+ 7.1 图的概念/Introduction of Graph  
+ 7.2 图的术语/Graph Terminology  
+ 7.3 图的表示与同构/Representing Graph and Graph Isomorphism  
+ 7.4 连通性/Connectivity  
+ 7.5 欧拉道路与哈密尔顿道路/Euler and Hamilton Paths  
+ 7.6 最短道路问题/Shortest Path Problem  
+ 7.7 平面图/Planar Graphs  
+ 7.8 图的着色/Graph Coloring

## 图的着色应用与对偶图

### DUAL GRAPH:

每一个 region 表示顶点，两个 region 有公共边界对应有一条边。

## 定义1：简单图的着色/coloring

每一个顶点指定一个颜色使得任意两个相邻顶点有不同的颜色。

## 定义2：简单图的色数/chromatic number

图的着色中使用的最小颜色数。

## 定理1

### 四着定理/four color theorem

任意一个图的色数小于等于 4。

## 应用问题

+ 1. SCHEDULING FINAL EXAMS  
+ 2. FREQUENCY ASSIGNMENT

## 小结

+ 1、平面图的概念：无向、简单、有限、非交叉边/区域  
+ 2、平面图的欧拉公式：必要条件  
+ 3、平面图判定的库氏定理：关键点：极大非平面图  
+ 4、图的着色和图的色数：

## 进一步的思考

+ 1、如何判断图中的极大非平面子图  
+ 2、如何对图中顶点着色---PAOWELL  
+ 3、进一步如何建立起对边的着色的一套方法

## Chapter 7 Graphs

## 图论

图/Graph：  
可直观地表示离散对象之间的相互关系，研究它们的共性和特性，以便解决具体问题。

## 7.1 图的概念/Introduction of Graph

## 7.2 图的术语/Graph Terminology

## 7.3 图的表示与同构/ Representing Graph and Graph Isomorphism

## 7.4 连通性/Connectivity

## 7.5 欧拉道路与哈密尔顿道路/ Euler and Hamilton Paths

## 7.6 最短道路问题/Shortest Path Problem

## 7.7 平面图/Planar Graphs

## 7.8 图的着色/Graph Coloring

