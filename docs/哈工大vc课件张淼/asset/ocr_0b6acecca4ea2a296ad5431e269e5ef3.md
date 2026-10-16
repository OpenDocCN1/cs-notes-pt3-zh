# 名空间（namespace）

可以把文件作用域的程序实体定义为一个局部于各个源文件的无名名空间。如：

```
namespace
{int x,y;}
```

等价于static的全局变量定义，如： static int x, y;