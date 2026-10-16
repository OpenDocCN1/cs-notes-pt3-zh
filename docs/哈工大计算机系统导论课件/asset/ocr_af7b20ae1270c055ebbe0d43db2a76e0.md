# malloc程序包

```
#include <stdlib.h>
```

```
void *malloc(size_t size)
```

+   - 成功:
+     - 返回已分配块的指针，块大小至少 size 字节，对齐方式依赖编译模式：8字节（32位模式），16字节（64位模式）
+     - If size == 0, returns NULL
+   - 出错: 返回 NULL (0)，同时设置 errno

```
void free(void *p)
```

+   - 将p指向的块返回到可用内存池
+   - p 必须 malloc、 realloc 或 calloc 已分配块的起止地址

# Other functions

+   - calloc: malloc的另一版本，将已分配块初始化为0.
+   - realloc: 改变之前分配块的大小.
+   - sbrk: 分配器隐含地扩展或收缩堆