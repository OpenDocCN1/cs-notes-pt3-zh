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