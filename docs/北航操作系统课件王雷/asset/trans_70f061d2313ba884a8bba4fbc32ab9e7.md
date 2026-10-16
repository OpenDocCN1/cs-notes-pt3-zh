
```
gcc program.c extras.c
./a.out
```

```
gcc -c program.c => program.o
gcc -c extras.c => extras.o
gcc program.o functions.o -o exe
./exe
```

![](img/861c0ad57b0249095c0356c9e5a83b26_1173_0.png)

从 /usr/lib/gcc-lib/i386-redhat-linux/2.96/specs 读取规格
gcc 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110)
/usr/lib/gcc-lib/i386-redhat-linux/2.96/cpp1 -lang-c -v -D__GNUC__=2 -D__GNUC_MINOR__=96 -D__GNUC_PATCHLEVEL__=0 -D__ELF__ -Dunix -Dlinux -D__ELF__ -D__unix__ -D__linux__ -D__unix -D__linux -Asystem(posix) -D__NO_INLINE__ -Acpu(i386) -Amachine(i386) -Di386 -D__i386 -D__i386__ -D__tune_i386__ main.c /tmp/ccdZzDrx.i
GNU CPP 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110) (cpp1)  i386 Linux/ELF)
忽略不存在的目录 "/usr/i386-redhat-linux/include"
#include "..." 搜索开始于此：
#include <...> 搜索开始于此：
/usr/local/include
/usr/lib/gcc-lib/i386-redhat-linux/2.96/include
/usr/include
搜索列表结束。
/usr/lib/gcc-lib/i386-redhat-linux/2.96/cc1 /tmp/ccdZzDrx.i -quiet -dumpbase main.c -version -o /tmp/ccO57GRS.s
GNU C 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110) (i386-redhat-linux) 由 GNU C 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110) 编译。
as -V -Qy -o /tmp/ccpAegkio /tmp/ccO57GRS.s
GNU 汇编器版本 2.11.93.0.2 (i386-redhat-linux) 使用 BFD 版本 2.11.93.0.2 20020207

/usr/lib/gcc-lib/i386-redhat-linux/2.96/cpp0 -lang-c -v -D__GNUC__=2 -D__GNUC_MINOR__=96 -D__GNUC_PATCHLEVEL__=0 -D__ELF__ -Dunix -Dlinux -D__ELF__ -D__unix__ -D__linux__ -D__unix -D__linux -Asystem(posix) -D__NO_INLINE__ -Acpu(i386) -Amachine(i386) -Di386 -D__i386 -D__i386__ -D__tune_i386__ extras.c
/tmp/ccdZzDrx.i
GNU CPP 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110) (cpplib, i386-redhat-linux/ELF)
忽略不存在的目录 "/usr/i386-redhat-linux/include"
#include "..." 搜索开始于此：
#include <...> 搜索开始于此：
/usr/local/include
/usr/lib/gcc-lib/i386-redhat-linux/2.96/include
/usr/include
搜索列表结束。
/usr/lib/gcc-lib/i386-redhat-linux/2.96/cc1 /tmp/ccdZzDrx.i -quiet -dumpbase extras.c -version -o /tmp/ccO57GRS.s
GNU C 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110) (i386-redhat-linux) 由
GNU C 版本 2.96 20000731 (Red Hat Linux 7.3 2.96-110) 编译。
as -V -Qy -o /tmp/cc2dnA1M.o /tmp/ccO57GRS.s
GNU 汇编器版本 2.11.92.0.2 (i386-redhat-linux) 使用 BFD 版本 2.11.93.0.2 20020207
/usr/lib/gcc-lib/i386-redhat-linux/2.96/collect2 -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -o exe /usr/lib/gcc-lib/i386-redhat-linux/2.96/.../crt1.o /usr/lib/gcc-lib/i386-redhat-linux/2.96/.../crti.o -L/usr/lib/gcc-lib/i386-redhat-linux/2.96 -L/usr/lib/gcc-lib/i386-redhat-linux/2.96/.../tmp/ccpAegki.o /tmp/cc2dnA1M.o -lgcc -lgcc /usr/lib/gcc-lib/i386-redhat-linux/2.96/crtend.o /usr/lib/gcc-lib/i386-redhat-linux/2.96/.../crtn.o

```
.file "program.c"
.section .rodata
.LC0:
    .string "I am done"
.text
.globl main
.type main,@function
main:
    pushl %ebp
    movl %esp,%ebp
    subl $8,%esp
    andl $-16,%esp
    movl $0,%eax
    subl %eax,%esp
    call read_something
    movl %eax,-4(%ebp)
    subl $12,%esp
    pushl -4(%ebp)
    call do_something
    addl $16,%esp
    movl %eax,some_global_variable
    subl $12,%esp
    pushl $.LC0
    call write_something
    addl $16,%esp
    leave
    ret
.Lfe1:
.size main,.Lfe1-main
.comm some_global_variable,4,4
.local some_local_variable
.comm some_local_variable,4,4
.ident "GCC: (GNU) 3.2.2 20030222 (Red Hat Linux 3.2.2-5)"
```

|  |  |
|---|---|
| ELF头 |  |
| 程序头表（可省略） |  |
| .text |  |
| .rodata |  |
| .data |  |
| ...... |  |
| 节头表 |  |

.bss　此节存放用于程序内存映象的未初始化数据。此节类型是 SHT_NOBITS，因此不占文件体空间。

.comment　此节存放版本控制信息。

.data和.data1　此节存放用于程序内存映象的初始化数据。

.debug　此节存放符号调试信息。

.dynamic　此节存放动态连接信息。

.dynstr　此节存放动态连接所需的字符串，在大多数情况下，这些字符串代表的是与符号表项有关的名字。

.dynsym　此节存放的是“符号表”中描述的动态链接符号表。

.fini　此节存放与进程中指代码有关的执行终止代码。

.got　此节存放全程偏移量表。

.hash　此节存放一个符号散列表。

.init　此节存放组成进程初始化代码的执行指令。

.interp　此节存放一个程序解释器的路径名。

.line　此节存放符号调试中的行号信息，主要描述源程序与机器指令之间的对应关系。

.note　此节存放提供兼容性、一致性的特殊信息。

.plt　此节存放过程链接表。

.relname和.rel.aname　此节存放重定位信息。

.rodata和.rodata1　此节存放进程映象中不可写的只读数据。

.shstrtab　此节存放节名。

.strtab　此节存放的字符串标识与符号表项有关的名字。

.symtab　此节存放符号表。

.text　此节存放正文，也称程序的执行指令。

