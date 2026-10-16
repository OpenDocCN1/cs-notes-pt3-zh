```
Z-Buffer()
[ 帧缓存全置为背景色
    for (屏幕上的每个像素(i, j)) //扫描整个屏幕
[ 深度缓存变量zb置最大值MaxValue
    for (多面体上的每个多边形Pk)
    { if (像素点(i, j)在pk的投影多边形之内)
    { 计算Pk在(i, j)处的深度值depth;
        if (depth小于zb)
        { zb = depth;
            indexp = k;}}}
    If (zb != MaxValue) 计算多边形Pindexp在交点 (i, j) 处的光照颜色并显示
]]
```