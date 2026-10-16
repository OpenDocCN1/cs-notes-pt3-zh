编写利用深度优先遍历算法求以邻接表存储的无向图的所有连通分量算法，要求输出每一连通分量的顶点值。

```
void dfs(v)
{visited[v]=true; printf ( "%3d",v); //输出连通分量的顶点。
p=g[v].firstarc;//g[v]顶点表
while (p!=null)
{  if (visited[p->adjvex]==false)  dfs(p->adjvex);
  p=p->next;
}
}
void Count()
  //求图中连通分量的个数
{
  int k=0 ; static AdjList g ; //设无向图g有n个结点
  for (i=1;i<=n;i++ )
    if (visited[i]==false) { printf ("\n第%d个连通分量:\n",++k); dfs(i);}
}
```