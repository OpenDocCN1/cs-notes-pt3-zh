
## 现代的解决方案:共享库

- 静态库有以下缺点:
  - 在保存的可执行文件中存在重复 (每个函数都需要libc)
  - 在运行的可执行文件中重复
  - 系统库的小错误修复要求每个应用程序显式地重新链接

- 现代的解决方案:共享库
  - 包含代码和数据的目标文件，在它们的加载时或运行时，被动态地加载并链接到应用程序中
  - 也称: 动态链接库, DLLs, .so 文件

## 共享库 (cont.)

- 当可执行文件第一次加载和运行时(加载时链接)，动态链接就会出现.
  - Linux的常见情况是，由动态链接器(`ld-linux.so`)自动处理.
  - 标准C库 (`libc.so`)通常采用动态链接的.

- 动态链接也可以在程序启动后进行(运行时链接).
  - 在Linux中，这是通过调用`dlopen()`接口完成的.

- 共享库的例程可以由多个进程共享.
  - 当我们学习虚拟内存时有更多关于这个的内容

## 在加载时的动态链接

main2.c vector.h

翻译器
/cpp, cc1, as/

main2.o

链接器 (ld)

prog21

加载器
/execve/

动态链接器(ld-linux.so)

```
unix> gcc -shared -o \
libvector.so addvec.c multvec.c
```

libc.so
libvector.so

重定位与符号表信息

可重定位
目标文件

可执行目标文件部分被链接

可执行程序在内存中被完全链接

libc.so
libvector.so

代码和数据

## 在运行时的动态链接

```c
#include <stdio.h>
#include <stdlib.h>
#include <dlfcn.h>

int x[2] = {1, 2};
int y[2] = {3, 4};
int z[2];

int main()
{
    void *handle;
    void (*addvec)(int *, int *, int *, int);
    char *error;

    /*动态加载包含addvec()的共享库*/
    handle = dlopen("./libvector.so", RTLD_LAZY);
    if (!handle) {
        fprintf(stderr, "%s\n", dlerror());
        exit(1);
    }
}
```

## 链接汇总

- 链接是一个技术： 允许从多个目标文件创建程序。
- 链接可以在程序的生命周期的不同时间发生:
  - 链接时(当程序被链接时) /GCC时（编译时）
  - 加载时(将程序加载到内存中)
  - 运行时(当程序正在执行时)
- 理解链接可以帮助你避免讨厌的错误，让你成为一个更优秀的程序员。

## 要点

- Linking
- 案例学习: 库打桩机制

## 案例学习: 库打桩机制

- 库打桩机制：强大的链接技术--- 允许程序员截获对任意函数的调用，取而代之执行自己的代码
- 打桩可出现在:
  - 编译时:源代码被编译的时候
  - 链接时:当可重定位目标文件被静态链接形成一个可执行目标文件的时候
  - 加载/运行时:当一个可执行目标文件被加载到内存中，动态链接，然后执行的时候

## 使用打桩机制

- 监控和性能分析
  - 追踪某个特殊函数的调用次数
  - 验证和追踪函数的输入和输出值
  - Malloc 跟踪
    - 检测内存泄露
    - 生成地址痕迹traces

## 程序实例

```
#include <stdio.h>
#include <malloc.h>

int main()
{
    int *p = malloc(32);
    free(p);
    return(0);
}
int.c
```

- 目标:跟踪经过分配和释放的内存块的地址和大小，不破坏程序，也不修改源代码
- 三个解决方案: 在编译时、链接时和加载/运行时对lib malloc和free函数进行打桩

## 编译时打桩

```
#ifdef COMPILE TIME
#include <stdio.h>
#include <malloc.h>

/* malloc wrapper function */
void *mymalloc(size_t size)
{
    void *ptr = malloc(size);
    printf("malloc(%d)=%p\n", (int)size, ptr);
    return ptr;
}

/* free wrapper function */
void myfree(void *ptr)
{
    free(ptr);
    printf("free(%p)\n", ptr);
}
#endif
```

## 编译时打桩

```c
#define malloc(size) mymalloc(size)
#define free(ptr) myfree(ptr)

void *mymalloc(size_t size);
void myfree(void *ptr);
```

```text
linux> make intc
gcc -Wall -DCOMPILETIME -c mymalloc.c
gcc -Wall -I. -o intc int.c mymalloc.o
linux> make runc
./intc
malloc(32)=0x1edc010
free(0x1edc010)
linux>
```

## 链接时打桩

```c
#ifdef LINKTIME
#include <stdio.h>

void *__real_malloc(size_t size);
void __real_free(void *ptr);

/* malloc wrapper function */
void *__wrap_malloc(size_t size)
{
    void *ptr = __real_malloc(size); /* Call libc malloc */
    printf("malloc(%d) = %p\n", (int)size, ptr);
    return ptr;
}

/* free wrapper function */
void __wrap_free(void *ptr)
{
    __real_free(ptr); /* Call libc free */
    printf("free(%p)\n", ptr);
}
#endif
```

## 链接时打桩

```text
linux> make intl
gcc -Wall -DLINKTIME -c mymalloc.c
gcc -Wall -c int.c
gcc -Wall -Wl,--wrap,malloc -Wl,--wrap,free -o intl int.o mymalloc.o
linux> make runl
./intl
malloc(32) = 0x1aa0010
free(0x1aa0010)
linux>
```

- **“--Wl”标志将参数传递给链接器，将每个逗号替换为空格**
- **“--wrap,malloc”参数** 指示链接器以一种特殊的方式解析引用：
  - 对 `malloc` 的引用，必须被解析为 `__wrap_malloc`
  - 对 `__real_malloc` 必须被解析为 `malloc`

## 加载/运行时打桩

```
#ifdef RUNTIME
#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>
#include <dlfcn.h>

/* malloc wrapper function */
void *malloc(size_t size)
{
    void *(*mallocp)(size_t size);
    char *error;

    mallocp = dlsym(RTLD_NEXT, "malloc"); /* Get addr of libc malloc */
    if ((error = dlerror()) != NULL) {
        fputs(error, stderr);
        exit(1);
    }
    char *ptr = mallocp(size); /* Call libc malloc */
    printf("malloc(%d) = %p\n", (int)size, ptr);
    return ptr;
}
mymalloc.c
```
