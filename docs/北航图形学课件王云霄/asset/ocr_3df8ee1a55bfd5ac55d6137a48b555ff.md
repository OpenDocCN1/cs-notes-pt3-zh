# （2）四连通边界定义区域填充算法：

```
void Boundaryfill(int x,int y,COLORREF boundaryvalue,COLORREF newvalue)
```

> /* (x, y) 为种子位置，boundaryvalue是边界象素值\nnewvalue是区域内象素新值，未填充前区域内不应有值为newvalue的象素。*/

```
{  if( GetPixel(x,y)!=boundaryvalue\n       && GetPixel(x,y)!=newvalue)   // 未达边界且未访问过
```