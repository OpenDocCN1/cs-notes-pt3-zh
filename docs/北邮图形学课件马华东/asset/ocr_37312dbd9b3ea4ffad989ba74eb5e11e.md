# 10.5.3 光照模式

+   - 全局环境光

使用下面函数来指定全局环境光的强度：
glLightModev(GL_LIGHT_MODEL_AMBIENT, GLfloat param)

+   - 观察点性质

定义观察点性质的函数是：
glLightModeli(GL_LIGHT_MODEL_LOCAL_VIEWER, glboolean param);
当参数param取GL_TRUE时,观察点为本地观察点；取GL_FALSE时,为无穷观察点。