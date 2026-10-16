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