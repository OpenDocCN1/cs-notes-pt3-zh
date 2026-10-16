# # OpenGL中的实体模型函数

+   - GLUT库中的二、三次曲面

+   - 绘制实体或线框球面
+   
+     ```c
+     void glutSolidSphere/glutWireSphere
+     (GLdouble radius, GLint slices, GLint stacks);
+     ```

+   - 绘制实体或线框圆锥面
+   
+     ```c
+     void glutSolidCone/glutWireCone
+     (GLdouble radius, GLdouble height, GLint
+     slices, GLint stacks);
+     ```