```
void DFS (AdjGraph G, int v, int visited [ ] ) {
cout << GetValue (G, v) << ' '; //访问顶点 v
visited[v] = 1; //顶点 v 作访问标记
int w = GetFirstNeighbor (G, v);
//取 v 的第一个邻接顶点 w
while ( w != -1 ) { //若邻接顶点 w 存在
if ( !visited[w] ) DFS (G, w, visited );
//若顶点 w 未访问过, 递归访问顶点 w
w = GetNextNeighbor (G, v, w );
//取顶点 v 排在 w 后的下一个邻接顶点
}
}
```