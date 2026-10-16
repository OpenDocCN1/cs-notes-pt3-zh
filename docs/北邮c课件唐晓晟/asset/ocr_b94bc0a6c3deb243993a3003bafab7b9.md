# 13.7 源代码组织

+   - 使用了模板的代码有两种明显的组织方式
+   - 在使用模板的编译单位最前面包含(include)有关模板的定义
+   - 只有在使用模板的编译单位最前面包含(include)有关模板的声明，并且分别编译它们的模板定义
+   - 此外，模板函数有时是首先声明，然后使用，最后在一个编译单位里定义

# 两种源代码组织方式示例(1)

```
//out.c
#include <iostream>
template<class T> void out(const T& t) { std::cerr<<t; }

//user1.c
#include "out.c"

//user2.c
#include "out.c"
```

out()的定义和它所依赖的有声明都# include在几个不同的编译单位里。(X)在需要对T生成代码时，会增大编译器必须处理的信息量同时也使得out()中的代码和用户代码相混。此外，某些元代码文件的读取过程将产生工作量和编译器额外负担。

# 两种源代码组织方式示例(2)

```
// out.h
template<class T> void out(const T& t);
// out.c
#include <iostream>
#include "out.h"
export template<class T> void out(const T& t){std::cerr<<t;}

//user1.c
#include "out.h"

//user2.c
#include "out.h"
```

这种模板被“放置”的处理与非内联函数处理一样。out()定义被单独进行编译。在需要该定义时，实际必须负责找到某一处的定义

# 源代码组织的理想方式

+   - 无论作为一个单独编译，还是分成一些独立的编译单元，这些代码都应该以同样的方式工作
+   - 接近这种理想的方式应该是限制模板定义对其环境的依赖性，而不是在进入实例化过程时为它的定义带上尽可能多的环境信息