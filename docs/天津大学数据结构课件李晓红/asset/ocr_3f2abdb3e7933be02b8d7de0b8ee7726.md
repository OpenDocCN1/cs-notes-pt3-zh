# # C语言描述

```
void BFSTraverse(ALGraph G,void(*Visit)(char*))
{\//按广度优先非递归遍历图G。使用辅助队列Q和访问标志数组visited。
    int v,u,w;
    VertexType u1,w1;
    LinkQueue Q;
    for(v=0;v<G.vexnum;++v)
        visited[v]=FALSE; // 置初值
    InitQueue(Q); // 置空的辅助队列Q
    for(v=0;v<G.vexnum;++v) // 如果是连通图,只v=0就遍历全图
        if(!visited[v]) // v尚未访问
        {
            visited[v]=TRUE;
            Visit(G.vertices[v].data);
            EnQueue(Q,v); // v入队列
            while(!QueueEmpty(Q)) // 队列不空
            {
                DeQueue(Q,u); // 队头元素出队并置为u
                strcpy(u1,GetVex(G,u));
                for(w=FirstAdjVex(G,u1);w>=0;w=NextAdjVex(G,u1,strcpy(w1,GetVex(G,w))))
                    if(!visited[w]) // w为u的尚未访问的邻接顶点
                    {
                        visited[w]=TRUE;
                        Visit(G.vertices[w].data);
                        EnQueue(Q,w); // w入队
                    }
            }
        }
    printf("\n");
}
```