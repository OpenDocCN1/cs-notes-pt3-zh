
## 5、B树和B+树

· B树和B+树

分裂之前：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_658_0.png)

力图变成：

![](img/af430dff16b82a0fe61ce7dee05dcf9c_658_1.png)

分裂之后：生成新结点 p′，将原结点的后半部分复制过去。若分裂一直进行到根，树可能长高一层。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_658_2.png)

## 5、B树和B+树

· B树和B+树
例如：3阶B树的插入操作。m=3, ⌈m/2⌉ -1 =1; 至少1个关键字，二个孩子结点。

7插入

![](img/af430dff16b82a0fe61ce7dee05dcf9c_659_0.png)

## 5、B-树和B+树

+   B 树和 B+ 树

例如：3阶 B 树的删除操作。m=3, ⌈m/2⌉-1=1; 至少 1 个关键字, 二个子节点。

借：通过相应的父亲节点向被删结点方向旋转

被删关键字

假定再删除该关键字

并

并

并

假定再删除该关键字

并：和父结点的 一个关键字、及邻居合并。有可能进行到根，使B树的深度降低一层！

## 5、B树和B+树

+   - B+ 树

+   - 定义： m 阶 B+ 树满足或空，或：

+   A、根结点要么是叶子，要么至少有两个儿子

+   B、除根结点和叶子结点之外，每个结点的儿子个数为： ⌈m/2⌉ <= s <= m

+   C、有 k 个儿子的非叶结点具有 k 个关键字

+   D、外部结点，保存信息。而叶结点可以认为是索引部分，结点中含其子树中的最大或最小结点关键字。

+   E、叶子结点包含关键字信息和指向相应记录的指针，且按关键字顺序相链结。

注意：参见下页，形结点称为外部结点或失败结点。它的父结点为叶子结点。

## 5、B树和B+树

例如：m = 3 阶 B+树。除根结点和叶子结点之外，每个结点的儿子个数至少为⌈m/2⌉ = 2 个；结点的关键字个数至少为 2。该 B+树的高为 4。叶子结点都在第 3 层上。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_663_0.png)

# B,B+

![](img/af430dff16b82a0fe61ce7dee05dcf9c_664_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_664_1.png)

B树的特性：

+   1. 关键字集合分布在整颗树中；
+   2. 任何一个关键字出现且只出现在一个结点中；
+   3. 搜索有可能在非叶子结点结束；
+   4. 其搜索性能等价于在关键字全集内做一次二分查找；
+   5. 自动层次控制；

B+的搜索与B树也基本相同，区别是B+树只有达到叶子结点才命中（B树可以在非叶子结点命中），其性能也等价于在关键字全集做一次二分查找；

B+的特性：

+   1. 所有关键字都出现在叶子结点的链表中（稠密索引），且链表中的关键字恰好是有序的；
+   2. 不可能在非叶子结点命中；
+   3. 非叶子结点相当于叶子结点的索引（稀疏索引），叶子结点相当于存储（关键字）数据的存储层；
+   4. 更适合文件索引系统；

B*树：更稠密，要求非根节点至少 2/3 填充，而不是 1/2

## 对比：索引顺序存取方法ISAM

磁盘是以盘组、柱面和磁道三级地址存取的设备

![](img/af430dff16b82a0fe61ce7dee05dcf9c_665_0.png)

图1.6 磁道、扇区与柱面示意图

## 5、B树和B+树

+   - B+树的應用： VSAM（Virtual Storage Access Method） 文件

+   - VSAM 文件原理图：

顺序索引 集合起点

控制面(控制区域)

控制区间

索引

B+树 索引 集合

顺序索引集合

数据集合

![](img/af430dff16b82a0fe61ce7dee05dcf9c_666_0.png)

## 5、B树和B+树

• 插入： 新记录进入控制区间，必须保证有序。

插入流程图：

查找新记录应插入的控制区间

新记录应插入后会导致该控制区间溢出吗？

新记录应插入到该控制区间

有空闲的控制区间好用吗？

取得新的控制区间。进行控制区间的分裂。将大约一半数据记录移入新的控制区间。修改顺序索引集合中相应的结点。将新记录插入到相应的控制区间。

取得新的控制面，进行控制面的分裂。将大约一半数据记录移入新的控制面；同时进行顺序索引集合中的相应结点的分裂。必要时，修改索引集合中的信息。 将新记录插入到相应的控制区间。

## 5、B树和B+树

+   - 删除：后面的节点向前移动把空间留给新插入的记录。控制区间变空，修改相应的顺序索引集合中的索引项。
+   - 优缺点：动态分配和释放存储，无需对文件进行重组，插入、查找快。空间利用率低，通常只有 50% ～ 70%。
+   - 加速的考虑：设置多个副本的顺序集合索引。

|  | 顺序集合索引 | 副本 | 副本 | 副本 |
|---|---|---|---|---|
| 1 道 |  |  |  |  |
| 2 道 | 控制区间 | 控制区间 | 控制区间 | 控制区间 |
| 3 道 | 控制区间 | 控制区间 | 控制区间 | 控制区间 |
|  | ... |  |  |  |

控制面的多个顺序索引集合

控制面

磁道 >>----<< 控制区间

## 5、B树和B+树

+   - 为什么称之为 VSAM 文件：虚拟存储，同机器、设备无关。

外部页面映射表

| 页面号 | 指针 |
| --- | --- |
| 1 |  |
| 2 |  |
| 3 |  |
| ... |  |

分页格式化磁盘组

![](img/af430dff16b82a0fe61ce7dee05dcf9c_670_0.png)

+   - 分页：把内外存按同样的大小进行分页。使文件技术不依赖于具体的外部设备。更换外设时，不必改变整个程序，只需改变外部页面映射表中的相对地址到绝对地址的计算程序即可。

+   - 控制区间＝若干页面。控制面＝若干控制区间。外存是内存的延伸，虚拟存储器。VSAM 可脱离具体的外部组织文件，所以称之为 VSAM 文件。

# Graphs

# Zhengwei QI

Most slides from Eric Roberts, CS 106B, Stanford

# # Examples of Graphs

![](img/af430dff16b82a0fe61ce7dee05dcf9c_672_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_672_1.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_672_2.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_672_3.png)

# Examples of Graphs

![](img/af430dff16b82a0fe61ce7dee05dcf9c_673_0.png)

# Transportation Graphs

![](img/af430dff16b82a0fe61ce7dee05dcf9c_674_0.png)

# The Definition of a Graph

+   - A *graph* consists of a set of *nodes* together with a set of *arcs*. The nodes correspond to the dots or circles in a graph diagram (which might be cities, words, neurons, or who knows what) and the arcs correspond to the links that connect two nodes.
+   - In some graphs, arcs are shown with an arrow that indicates the direction in which two nodes are linked. Such graphs are called *directed graphs*.
+   - Other graphs, arcs are simple connections indicating that one can move in either direction between the two nodes. These graphs are *undirected graphs*.
+   - Question: Which of these two structures is more general?
