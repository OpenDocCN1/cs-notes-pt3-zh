

# 图 6.36

![](img/15e8d7d94d8ddf02cb6839870195a31e_551_0.png)

定义：在 AOV 网络 G 中，若从 i 到 j 存在一条有向路径，则称顶点 i 是 j 的前驱。若 <i, j> 是 G 中的一条边，则 i 是 j 的直接前驱，j 是 i 的直接后继。

定义：既是传递的又是反自反的优先关系是一个偏序。

没有环的有向图是有向无环图。

给定一个 AOV 网络 G，我们关心的是确定它是否反自反，即是否无环。

并且我们需要生成 G 中顶点的拓扑顺序。

## 定义：拓扑顺序是图的顶点的一种线性排序，使得对于网络中任意两个顶点 i 和 j，如果 i 是 j 的前驱，则在该线性排序中 i 在 j 之前。

图 6.36 的两种可能的拓扑顺序是：

- 1. C1,C2,C4,C5,C3,C6,C8,C7,C10,C13,C12,C14,C15,C11,C9
- 2. C4,C5,C2,C1,C6,C3,C8,C15,C7,C9,C10,C11,C12,C13,C14

# 拓扑排序算法

思路：列出一个没有前驱的顶点，然后从网络中删除该顶点以及从它引出的所有边。重复上述操作，直到所有顶点都被列出或所有剩余顶点都有前驱。

# 形式化描述，

```
1 Input the AOV network, let n be the number of vertices;
2 for (int i=0; i<n; i++) // output the vertices
3 {
4   if (every vertex has a predecessor) return;
5   // network has a cycle and is infeasible.
6   pick a vertex v that has no predecessors;
7   cout << v;
8   delete v and all edges leading out of v from the network;
9 }
```

# 示例：

![](img/15e8d7d94d8ddf02cb6839870195a31e_557_0.png)

图 6.37
(a) 初始

![](img/15e8d7d94d8ddf02cb6839870195a31e_558_0.png)

(b) 顶点 0 被删除

(c) 顶点 3 被删除

生成的拓扑顺序：0, 3,

![](img/15e8d7d94d8ddf02cb6839870195a31e_559_0.png)

(d) 顶点 2 被删除

(e) 顶点 5 被删除

(f) 顶点 1 被删除

生成的拓扑顺序：0, 3, 2, 5, 1, 4

# 数据表示取决于：

- (1) 一个顶点是否有前驱？--- 维护每个顶点的直接前驱数量的计数。
- (2) 如何删除一个顶点及其所有关联边？--- 邻接表，并减少其邻接表上所有顶点的计数。

每当一个顶点的计数降为 0 时，该顶点就可以被放入计数为 0 的顶点列表中。

因此，我们使用邻接表表示，并假设：

- **int *count** 被定义为一个数据成员，并在构造函数中分配其空间。
- count[i]，0≤i<n，已被初始化为顶点 i 的入度。当输入 <i, j> 时，j 的计数增加 1。
- 计数为 0 的顶点列表通过 **count** 字段维护为自定义栈，因为计数变为 0 后该字段不再使用。

```
1 void LinkedGraph::TopologicalOrder()
2 { //The n vertices of a network are listed in topological order
3   int top = -1, pos = 0;
4   for (int i=0; i<n; i++) //create a linked stack of vertices with
5     if (count[i]==0) { count[i]=top;  top=i;} //no predecessors
6   for (i=0; i<n; i++)
7     if (top==-1) throw "network has a cycle.";
8     int j=top;  top=count[top]; //unstack a vertex
9     t[pos++] = j;  // store vertex j in topological order
10    Chain<int>::ChainIterator ji=adjLists[j].begin();
11    while (ji != adjLists[j].end()) { // decrease the count of
12      count[*ji]--;
13      // the successor vertices of j
14      if (count[*ji]==0) {count[*ji]=top; top=*ji;} //add to stack
15      ji++; // next successor
16    }
17 }
```

# TopologicalOrder 的分析：

由于数据结构的明智选择，非常高效。

- 第 4-5 行循环：O(n)
- 第 6-10 行总计 O(n)
- 第 11-15 行的 while 循环对每个顶点 i 耗时 O(dᵢ)，其中 dᵢ 是 i 的出度。这部分的总时间为 O((∑ᵢ₌₀ⁿ⁻¹ dᵢ)+n)=O(e+n)。

总时间：O(e+n)。

