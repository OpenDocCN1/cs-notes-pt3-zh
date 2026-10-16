# # OpenGL中层次模型的实现

+   - 多级显示列表

OpenGL支持创建多级显示列表，即在 glNewList 和 glEndList 函数对之间允许调用 glCallList 函数来执行其他显示列表。

+   - 显示列表的删除

```
void glDeleteLists(GLuint listID, GLsizei range);
```