

# 练习3

BT[1: 15]

| A | B | D | I | C |  | E | F |  |  | G |  |  |  | H |

![](img/f94080b0b6a6124b22e8484de896d7b7_302_0.png)

前序序列： ABIFCGDEH

中序序列： FIBCGADEH

后序序列： FIGCBHEDA

# 练习4

已知二叉树采用二叉链表存储结构, 根结点地址为T, 写一算法, 删除数据域内容为item 的结点以及以该结点为根的子树上的所有结点.

假设item=1

![](img/f94080b0b6a6124b22e8484de896d7b7_303_0.png)

```
procedure PREORDER(T)
    if (T=nil) then
        return
    top←0
    p←T
    repeat
        while (p≠nil) do
            call VISIT(p)
            if (top=M) then
                [ call ERROR('overflow!')
                  return ]
            top←top+1
            STACK[top]←p
            p←lchild(p)
        end
        p←STACK[top]
        top←top-1
        p←rchild(p)
    until (p=nil and top=0)
end
```

![](img/f94080b0b6a6124b22e8484de896d7b7_305_0.png)

```
if (data(p)=item) then
  if (p=T) then
    T ←nil
  else
    if (lchild(q)=p) then
      lchild(q)←nil
    else
      rchild(q)←nil
call RELEASE(p)
return
```

![](img/f94080b0b6a6124b22e8484de896d7b7_306_0.png)

```
procedure DEL(T, item)
if (T=nil) then
  return
top←0
p←T
repeat
  while (p≠nil) do
    call VISIT(p)
    if (top=M) then
      call ERROR('overflow!')
      return
    top←top+1
    STACK[top]←p
    q←p
    p←lchild(p)
  end
  p←STACK[top]
  top←top-1
  q←p
  p←rchild(p)
until (p=nil and top=0)
end
```

# 练习5

已知二叉树的前序序列与中序序列分别存放与数组PREOD[1:n]与INOD[1:n]中，并且各节点的数据信息均不相同，请写一算法，生成该二叉树的二叉链表存储结构。

![](img/f94080b0b6a6124b22e8484de896d7b7_308_0.png)

前序序列：PREOD[1:9]

`A B D E J C F I G`

中序序列：INOD[1:9]

`D B J E A F I C G`

# 利用二叉排序树的“逐点插入法”

前序序列: PREOD[1:9]

A B D E J C F I G

中序序列: INOD[1:9]

D B J E A F I C G
1 2 3 4 5 6 7 8 9

前序序列中的结点在中序序列中的位置:

5 2 1 4 3 8 6 7 9

依次将前序序列中的结点按照在中序序列中位置大小插入到二叉树中。

# [INOD[i] 表示中序序列，\nitem 表示序列中一个元素

```
function SEARCHPOS(INOD, n, item)
    for i←1 to n do
        if (INOD[i]=item) then
            return(i)
        end
    end
```

> 求item在序列INOD中的位置

# 主算法

若已知中序序列 IN[1:n]和后序序列 POST[1:n]，又如何

```
procedure BUILDTREE( T )
T←nil
for i←1 to n do
    call INSERTITEM( T, PREOD[i] )
end
end
```

```
for i←n downto 1 do
    call INSERTITEM( T, POSTOD[i] )
end
```

# 第八章

# 冬

一个数据元素——顶点。

数据元素(顶点)之间的关系——边(弧)

# 本章讨论的主要内容：

+   - 8.1 图的基本概念
+   - 8.2 图的存储方法
+   - 8.3 图的遍历
+   - 8.4 最小生成树
+   - 8.5 最短路径问题
+   - 8.6 AOV网与拓扑排序
+   - 8.7 AOE网与关键路径

# 关于一条边或弧的表示方法：

(1). 用图形：

![](img/f94080b0b6a6124b22e8484de896d7b7_317_0.png)

(2). 用符号：

(Vi, Vj)

顶点偶对

(3). 用语言：

+   - 顶点Vi与Vj是这条边的两个邻接点。
+   - 这条边依附于顶点Vi和顶点Vj。

![](img/f94080b0b6a6124b22e8484de896d7b7_318_0.png)

![](img/f94080b0b6a6124b22e8484de896d7b7_318_1.png)

# G₁=(V₁, E₁)

# G₂=(V₂, E₂)

其中

其中

V₁ = { v₁, v₂, v₃, v₄ }

V₂ = { v₁, v₂, v₃, v₄ }

E₁ = { (v₁,v₂), (v₁,v₃), (v₁,v₄), (v₂,v₃), (v₂,v₄), (v₃,v₄) }

E₂ = { <v₁,v₂>, <v₂,v₁>, <v₂,v₃>, <v₄,v₃> }

# 二. 图的分类

无向图 对于 (v_i, v_j)∈E, 必有 (v_j, v_i)∈E, 并且偶对中顶点的前后顺序无关。

有向图 若 <v_i, v_j>∈E 是顶点的有序偶对。

网(络) 与边有关的数据称为权, 边上带权的图称为网络。

![](img/f94080b0b6a6124b22e8484de896d7b7_319_0.png)

![](img/f94080b0b6a6124b22e8484de896d7b7_319_1.png)

![](img/f94080b0b6a6124b22e8484de896d7b7_319_2.png)

# 三. 名词术语

# 1. 顶点的度

依附于顶点vᵢ的边的数目, 记为TD(vᵢ).

对于有向图而言, 有:

顶点的出度:

以顶点vᵢ为出发点的边的数目, 记为OD(vᵢ).

顶点的入度:

以顶点vᵢ为终止点的边的数目, 记为ID(vᵢ).

TD(vᵢ) = OD(vᵢ) + ID(vᵢ)

![](img/f94080b0b6a6124b22e8484de896d7b7_320_0.png)

![](img/f94080b0b6a6124b22e8484de896d7b7_320_1.png)

# 结论1

对于具有n个顶点, e条边的图, 有
2e = Σᵢ₌₁ⁿ TD(vᵢ)

# 结论2

具有n个顶点的无向图最多有n(n-1)/2 条边。

# 结论3

具有n个顶点的有向图最多有n(n-1) 条边。

边的数目达到最大的图称为完全图。边的数目达到或接近最大的图称为稠密图, 否则, 称为稀疏图。

# 2. 路径

顶点vₓ到vᵧ之间有路径P(vₓ, vᵧ)的充分必要条件为：存在顶点序列 vₓ, vᵢ₁, vᵢ₂, …, vᵢₘ, vᵧ, 并且序列中相邻两个顶点构造的顶点偶对分别为图中的一条边。

![](img/f94080b0b6a6124b22e8484de896d7b7_322_0.png)

P(A, E): A, B, E
A, C, D, E

出发点与终止点相同的路径称为回路或环；顶点序列中顶点不重复出现的路径称为简单路径。不带权的图的路径长度是指路径上所经过的边的数目，带权的图的路径长度是指路径上经过的边上的权值之和。

