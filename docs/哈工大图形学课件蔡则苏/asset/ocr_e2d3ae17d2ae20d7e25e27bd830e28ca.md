# OpenGL程序实例——绘制图形

+   - 刷新窗口的缓冲区（ glClear）
+   - 设定投影参数
+     ```
+     glMatrixMode(GL_PROJECTION);
+     gluOrtho2D(0.0,200.0,0.0,150.0);
+     ```
+   - 绘制图形
+     ```
+     glRectf(50.0f, 100.0f, 150.0f, 50.0f);
+     ```