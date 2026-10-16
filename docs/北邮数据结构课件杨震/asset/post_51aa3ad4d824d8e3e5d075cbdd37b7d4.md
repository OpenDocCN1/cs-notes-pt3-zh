
# （2）十字链表 顺序存储+链式存储 G₂

适用对象：有向图。

# [例]

顶点线性表

弧的十字链表(弧头、弧尾)

data
firstin
firstout

tailvex
headvex
weight
tlink
hlink

查询入边和出边比较容易！

![](img/808bb2589300c03793be19c880a932f9_337_0.png)

![](img/808bb2589300c03793be19c880a932f9_337_1.png)

# （3）邻接多重表 顺序存储+链式存储

适用对象：无向图。

特点：方便无向图中对边的操作。

# [例]

顶点线性表 邻接多重表

mark ivex ilink jvex jlink

data firstedge

![](img/808bb2589300c03793be19c880a932f9_338_0.png)

![](img/808bb2589300c03793be19c880a932f9_338_1.png)

边表中的边节点只需存放一次，节约内存。

# 7.3 图的遍历

# 两种遍历方式

- 深度优先遍历（树的先根遍历的推广）
- 广度优先遍历（树的按层次遍历的推广）

# 1. 深度优先遍历

**注意：** 每个顶点只能被访问一次，因为一个顶点可以和其它的任何顶点相邻接，为了避免对一个顶点的重复访问，必须对访问过的顶点加以标记。顶点的邻接顶点的次序是任意的，因此深度优先搜索的序列可能有多种。

# [遍历过程]

- 1、选中第一个被访问的顶点。
- 2、对顶点作已访问过的标志。
- 3、依次从顶点的未被访问过、邻接顶点出发，进行深度优先遍历。转向2。
- 4、如果还有顶点未被访问，则选中一个起始顶点，转向2。
- 5、所有的顶点都被访问到，则结束。

数据结构：主——图的存储结构

辅——数组 visited[1..n] //用于标识结点是否已被访问过

# [例]无向图的深度优先遍历

![](img/808bb2589300c03793be19c880a932f9_340_0.png)

设从v₁出发遍历

深度：v₁ v₂ v₄ v₈ v₅ v₆ v₃ v₇

广度：v₁ v₂ v₃ v₄ v₅ v₆ v₇ v₈

# [例] 有向图的深度优先遍历

从顶点 1 出发的搜索序列：

1、2、3、4；没有搜索到所有的顶点，必须另选图中未访问过的结点，继续进行搜索。

从顶点 5 出发的搜索序列：

5、6、2、3、1、4、7

适用的数据结构：栈

# [算法实现]

(1)访问顶点v，并记录v已被访问

(2)依次从v的未访问的邻接点出发，深度优先搜索图G。

```
void DFSTraverse( Graph G, Status ( * VisitFunc) (int v));
{ VisitFunc = Visit;
    for ( v=0; v <G.vexnum; ++v ) visited[v] = false;
    for ( v=0; v <G.vexnum; ++v )
        if ( ! Visited[ v ] ) DFS(G, v )
}
```

```
void DFS( Graph G, int v );
{ Visited[v] = true; VisitFunc(v);
    for ( w = FirstAdjVex(G, v) ; w ; w = NextAdjVex(G, v, w) )
        if ( ! Visited[ w ] ) DFS(G, w )
}
```

# [算法时间复杂度分析]

主要操作：查找每个顶点的所有邻接点

- 邻接矩阵 O(n²)
- 邻接表 无向图 O(n+2e)
- 有向图 O(n+e)

思考：如果对于图而言，深度优先遍历可以判断其是否有环吗？

可以。 dfs（v）结束前出现顶点u到v的回边，则图中必有包含顶点v和u的回路

# [非递归的算法思想]

- (1) 访问一个顶点，并记录它已被访问；
  将它的所有未访问的邻接顶点入栈；
- (2) 如果栈空，则退出；
  否则，栈中一顶点出栈；
- (3) 如果该顶点已被访问过，则转(2)
  否则，转(1)

# [非递归的算法实现]

```
void Traver(AdjList g,vertype v)
//图g以邻接表为存储结构，算法从顶点v开始实现非递归深度优先遍历。
{struct arc *stack[];
    visited[v]=1; printf(v); //输出顶点v
    top=0; p=g[v].firstarc; stack[++top]=p;
    while(top>0 || p!=NULL)
    {
        while (p)
            if (p && visited[p->adjvex]) p=p->next;
            else {printf(p->adjvex); visited[p->adjvex]=1;
                stack[++top]=p; p=g[p->adjvex].firstarc;}//else
        if (top>0) {p=stack[top--]; p=p->next; }
    }//while
}//算法结束。
```

算法讨论：以上算法适合连通图，若是非连通图，则再增加一个主调算法,其核心语句是for (vi=1;vi<=n;vi++) if (!visited[vi]) Traver(g,vi);

树：

树的按层次进行访问的次序：

A、B、C、D、E、F、G、H、
I、J、K、L

适用的数据结构：队列

# 队列的变化：

- 1、A进队
- 2、A出队、访问，队空
- 3、A的孩子结点进队
- 4、B出队、访问
- 5、B的孩子结点进队
- 6、C出队、访问
- 7、C的孩子结点进队
- 。。。。。。

![](img/808bb2589300c03793be19c880a932f9_347_0.png)

![](img/808bb2589300c03793be19c880a932f9_347_1.png)

# [算法思想]

- (1)访问顶点v，并记录它已被访问；
      顶点v入队列；
- (2)如果队列空，则退出；
      否则，从队中取出一个顶点；
- (3)求该顶点的一个邻接点；
      如果此邻接点未被访问，
      则访问它，并记录它已被访问，将其入队列；
- (4)如果该顶点还有下一个邻接点，则转(3)；
      否则，转(2)

```
void BFSTraverse( Graph G, Status ( * VisitFunc) (int v))
{ VisitFunc = Visit;
    for ( v=0; v <G.vexnum; ++v ) visited[v] = FALSE;
    InitQueue(Q);
    for ( v=0; v <G.vexnum; ++v )
        if ( ! Visited[ v ] )
        { Visited[ v ] = TRUE; Visit(v); EnQueue(Q,v);
        while (!EmptyQueue(Q))
        { DeQueue(Q,u);
            for ( w = FirstAdjVex(G, u) ; w ; w = NextAdjVex(G, u, w) )
                if ( ! Visited[ w ] )
                { Visited[ v ] = TRUE; Visit(v); EnQueue(Q, w) };
        }
}
```

# [算法时间复杂度分析]

主要操作：查找每个顶点的所有邻接点

- 邻接矩阵 O(n²)
- 邻接表 无向图 O(n+2e)
- 有向图 O(n+e)

# 3 图的遍历小结

- 深度优先遍历算法借助于栈结构实现；广度优先遍历算法借助于队列结构实现
- 图的遍历序列与算法和存储方式有关
- 对于非连通图，通过遍历可求得各连通分量

```
```c
void find_cycle() //判断是否有回路，有则输出邻接矩阵。visited数组为全局变量。
{
    for (i=1;i<=n;i++) visited[i]=0;
    for (i=1;i<=n;i++) if (!visited[i]) dfs(i);
}//find_cycle
void dfs(int v)
{
    visited[v]=1;
    for(j=1;j<=n;j++)
        if (g[v][j]!=0) //存在边(v,j)
            if (visited[j]!=1) {if (!visited[j]) dfs(j);}
            else {cycle=1; Print(i,j);}
    visited[v]=2;
}
void Print(int v,int start) //输出从顶点start开始的回路。
{
    for(i=1;i<=n;i++)
        if(g[v][i]!=0 && visited[i]==1) //若存在边(v,i)，且顶点i的状态为1。
        {
            printf("%d",v);
            if(i==start) printf("\n");
            else Print(i,start);
            break;
        }
}//Print
```
```

有向图判断回路要比无向图复杂。利用深度优先遍历，将顶点分成三类：未访问；已访问但其邻接点未访问完；已访问且其邻接点已访问完。用0、1、2表示这三种状态。若dfs（v）结束前出现顶点u到v的回边，则图中必有包含顶点v和u的回路。对应程序中v的状态为1，而u是正访问的顶点，若我们找出u的下一邻接点的状态为1，就可以输出回路了。
