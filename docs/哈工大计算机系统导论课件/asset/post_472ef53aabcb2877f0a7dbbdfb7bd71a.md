
## 在运行时的动态链接

```
/* 获取我们刚刚加载的addvec()函数的指针 */
addvec = dlsym(handle, "addvec");
if ((error = dlerror()) != NULL) {
    fprintf(stderr, "%s\n", error);
    exit(1);
}

/*现在我们就可以像其他函数一样调用addvec() */
addvec(x, y, z, 2);
printf("z = [%d %d]\n", z[0], z[1]);

/*卸载共享库*/
if (dlclose(handle) < 0) {
    fprintf(stderr, "%s\n", dlerror());
    exit(1);
}
return 0;
}
```

## 位置无关代码（PIC）

- 动态链接用到一个重要概念：
  - 位置无关代码（Position-Independent Code，PIC）
  - GCC选项 -fPIC指示生成PIC代码
- 共享库代码是一种PIC
  - 共享库代码的位置可以是不确定的
  - 即使共享库代码的长度发生变化，也不影响调用它的程序
- 引入PIC的目的
  - 链接器无需修改代码即可将共享库加载到任意地址运行
- 所有引用情况
  1. 模块内的过程调用、跳转，采用PC相对偏移寻址
  2. 模块内数据访问，如模块内的全局变量和静态变量
  3. 模块外的过程调用、跳转
  4. 模块外的数据访问，如外部变量的访问

要实现动态链接，必须生成PIC代码。

要生成PIC代码，主要解决这两个问题。

## 可执行文件的加载

- 通过调用 execve 系统调用函数来调用加载器
- 加载器（loader）根据可执行文件的程序（段）头表中的信息，将可执行文件的代码和数据从磁盘“拷贝”到存储器中（实际上不会真正拷贝，仅建立一种映射，这涉及到许多复杂的过程和一些重要概念，将在后续课上学习）
- 加载后，将PC（EIP）设定指向 Entry point（即符号 _start处），最终执行 main 函数，以启动程序执行

程序被启动，如 `$ ./hello`

调用 fork()

以构造的 argv 和 envp 为参数调用 execve()

execve() 调用加载器进行可执行文件加载，并最终转去执行 main

```
_start: __libc_init_first → _init → atexit → main → _exit
```

## ELF头信息举例

```
$ readelf -h main
```

ELF Header:
Magic: 7f 45 4c 46 01 01 01 00 00 00 ...
Class: ELF32
Data: 2's complement, little endian
Version: 1 (current)
OS/ABI: UNIX - System V
ABI Version: 0
Type: EXEC (Executable file)
Machine: Intel 80386
Version: 0x1
Entry point address: 0x8048580
Start of program headers: 52 (bytes into file)
Start of section headers: 3232 (bytes into file)
Flags: 0x0
Size of this header: 52 (bytes)
Size of program headers: 32 (bytes)
Number of program headers: 8
Size of section headers: 40 (bytes)
Number of section headers: 29
Section header string table index: 26

注意：程序入口地址并不是 0x8048000

![](img/7ab811dea080313a753fa0ae68528fa9_1246_0.png)

## 程序的加载和运行

- UNIX/Linux系统中，可通过调用execve()函数来启动加载器。
- execve()函数的功能是在当前进程上下文中加载并运行一个新程序。execve()函数的用法如下：
  - `int execve(char *filename, char *argv[], char *envp[]);`
  - filename是加载并运行的可执行文件名（如./hello），可带参数列表argv和环境变量列表envp。若错误（如找不到指定文件filename），则返回-1，并将控制权交给调用程序；若函数执行成功，则不返回，最终将控制权传递到可执行目标中的主函数main。
- 主函数main()的原型形式如下：
  - `int main(int argc, char **argv, char **envp);` 或者：
  - `int main(int argc, char *argv[], char *envp[]);`
  - argc指定参数个数，参数列表中第一个总是命令行（可执行文件名）
  - 例如：命令行为 “ld -o test main.o test.o” 时，argc=6

问题：hello程序的加载和运行过程是怎样的？

1. Step1：在shell命令行提示符后输入命令：`$ ./hello[enter]`
2. Step2：shell命令行解释器构造argv和envp

   ![](img/7ab811dea080313a753fa0ae68528fa9_1248_0.png)

3. Step3：调用fork()函数，创建一个子进程，与父进程shell完全相同（只读/共享），包括只读代码段、可读写数据段、堆以及用户栈等。
4. Step4：调用execve()函数，在当前进程（新创建的子进程）的上下文中加载并运行hello程序。将hello中的.text节、.data节、.bss节等内容加载到当前进程的虚拟地址空间（仅修改当前进程上下文中关于存储映射的一些数据结构，不从磁盘拷贝代码、数据等内容）
5. Step5：调用hello程序的main()函数，hello程序开始在一个进程的上下文中运行。

```
int main(int argc, char *argv[], char *envp[])
```

## 链接汇总

- 链接是一个技术：允许从多个目标文件创建程序。

- 链接可以在程序的生命周期的不同时间发生:
  - 链接时（当程序被链接时）/GCC时（编译时）
  - 加载时（将程序加载到内存中）
  - 运行时（当程序正在执行时）

- 理解链接可以帮助你避免讨厌的错误，让你成为一个更优秀的程序员。

## 要点

- Linking
- 案例学习: 库打桩机制

### 案例学习: 库打桩机制

- 库打桩机制：强大的链接技术--- 允许程序员截获对任意函数的调用，取而代之执行自己的代码
- 打桩可出现在：
  - 编译时：源代码被编译的时候
  - 链接时：当可重定位目标文件被静态链接形成一个可执行目标文件的时候
  - 加载/运行时：当一个可执行目标文件被加载到内存中，动态链接，然后执行的时候

### 使用打桩机制

- 监控和性能分析
  - 追踪某个特殊函数的调用次数
  - 验证和追踪函数的输入和输出值
  - Malloc 跟踪
    - 检测内存泄露
    - 生成地址痕迹traces

### 程序实例

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

目标：跟踪经过分配和释放的内存块的地址和大小，不破坏程序，也不修改源代码。

三个解决方案：在编译时、链接时和加载/运行时对lib malloc和free函数进行打桩。

### 编译时打桩

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
