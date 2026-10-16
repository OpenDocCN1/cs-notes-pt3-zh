# 采用数组表示法构造无向网的算法:

```
```
Status CreateUDN(Mgraph &G)
{
	Scanf(&G.vexnum,&G.arcnum,&incinfo);
	For(i=0;i<G.vexnum;i++) scanf(&G.vexs[i]);
	For(i=0;i<G.vexnum;i++)
	For(j=0;j<G.vexnum;j++)
	G.arcs[i][j]={0, NULL}; //矩阵的初始化
	For(k=0;k<G.arcnum;k++)
	{
		Scanf(&v1,&v2,&w);
		i=LocateVex(G,v1);j=LocateVex(G,v2);
		G.arcs[i][j].adj=w;
		if(incinfo) input(*G.arcs [i][j].info);
	}
}
```
```