# # 多边形面的属性

+   - 多边形面的填充

多边形面既可以用纯色填充，也可以用  
\( 32 \times 32 \) 的模板位图来填充。

```
void glPolygonStipple(const GLubyte *mask);
glEnable(GL_POLYGON_STIPPLE);
```