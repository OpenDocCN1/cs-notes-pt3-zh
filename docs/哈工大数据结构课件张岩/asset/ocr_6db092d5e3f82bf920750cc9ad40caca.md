# 4.3 图的搜索（遍历）(cont.)

广度优先遍历主算法：

```
bool visited[NumVertices]; //访问标记数组是全局变量
int dfn[NumVertices]; //顶点的先深编号
void BFSTraverse (AdjGraph G)   //主算法
/* 先广搜索一邻接表表示的图G； 而以邻接矩阵表示G时，算法完全相同 */
{
    int i, count = 1;
    for ( int i = 0; i < G.n; i++ )
        visited [i] = FALSE;  //标志数组初始化
    for ( int i = 0; i < G.n; i++ )
        if ( ! visited[i] )
            BFSX ( G, i ); //从顶点 i 出发的一次搜索， DFSX (G, i)
}
```