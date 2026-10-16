# OpenGL中的实体模型函数

+   - GLU二次曲面函数
+     - 定义一个二次曲面
+       `GLUquadricObj *sphere;`
+     - 激活二次曲面绘制器
+       `sphere = gluNewQuadric();`
+     - 指定二次曲面的绘制方式
+       `gluQuadricDrawStyle(sphere, GLU_LINE);`