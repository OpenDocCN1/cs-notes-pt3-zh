# 10.1.2 OpenGL的API结构

图10.1(a)是Win32平台上OpenGL API的结构简图；(b)是UNIX平台上OpenGL API的结构简图。其中

+   - “OpenGL”表示OpenGL基本API, 功能包括：
+     物体描述、平移、旋转、光照、纹理、文字等；
+   - “GLU”表示实用API, 功能包括: 绘制二次曲面、NURBS曲面、复杂多边形及纹理、矩阵管理等；
+   - “WGL”是Win32为支持OpenGL而设计的编程接口；
+   - “GLX”是UNIX系统支持OpenGL的编程接口