# OpenGL中的反走样

颜色混和函数用于计算两个互相重叠的对象 的颜色。

在RGBA颜色模式（A表示透明度）中，已知源像素的颜色值为（Sr，Sg，Sb，Sa），目标像素的颜色值为（Dr，Dg，Db，Da），颜色混合后像素的颜色为：

```
(Rs.Sr + Rd.Dr, Gs.Sg + Gd.Dg, Bs.Sb + Bd.Db, As.Sa + Ad.Da)
```