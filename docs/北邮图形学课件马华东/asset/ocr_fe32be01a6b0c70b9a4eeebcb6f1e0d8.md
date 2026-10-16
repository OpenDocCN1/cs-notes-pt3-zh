# 10.5.2 光源定义

定义光源主要就是定义它的各种特性。可用来下面函数定义：

```
void glLight{if}[v](GLenum light, GLenum pname, TYPE param);
```

*light*用形式为GL_LIGHTi的符号常量表示, 0≤i≤8;
*pname*设置光源的特性;
*param*设置*pname*特性的值.
光源定义后, 须调用glEnable()打开该光源。