# 10.4.4 投影变换

# 透视投影

其取景体是一个截头锥体, 可用 glFrustum() 函数定义这个截头锥体:

```
void glFrustum(GLdouble left, GLdouble right, GLdouble bottom, GLdouble top, GLdouble near, GLdouble far);
```

该函数以透视矩阵乘当前矩阵。

+   - *left, right* 指定左右垂直裁剪面的坐标；
+   - *bottom, top* 指定底和顶水平裁剪面的坐标；
+   - *near, far* 指定近和远深度裁剪面的距离。