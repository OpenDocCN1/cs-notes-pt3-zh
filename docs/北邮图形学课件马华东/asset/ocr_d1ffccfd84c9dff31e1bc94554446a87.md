# 10.2.5 一个简单的程序

```
```cpp
#include <windows.h>
#include <gl\glut.h>
void RenderScene()
{
    glClear(GL_COLOR_BUFFER_BIT); //清颜色缓冲区
    // --绘图命令函数--
    glFlush(); //绘图结果显示到屏幕上
}
void SetupRC()
{
    glClearColor(0.0f, 0.0f, 1.0f, 1.0f); //设置背景色
}
```
```