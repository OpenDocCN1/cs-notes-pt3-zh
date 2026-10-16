# OpenGL中的反走样

+   - 启用反走样
+     `glEnable(primitiveType);`
+   - 启用OpenGL颜色混和并指定颜色混合函数
+     `glEnable(GL_BLEND);`
+     `glBlendFunc(GL_SCR_ALPHA, GL_ONE_MINUS_SRC_ALPHA);`