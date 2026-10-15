

## 案例 2

+   - 请在父进程和子进程执行完毕之前，将下面的 PPN 填入平页表中。

父进程：子进程：

第 4 页 栈

第 5 页 第 1 页 PPN：3

栈 第 3 页

第 0 页 Bss PPN：1 PPN：0

第 2 页 第 0 页

Bss 第 2 页 PPN：8 PPN：7

堆 堆 PPN：6 PPN：11 PPN：4

Fork

第 1 页

父进程

栈 47

第 5 页 第 4 页 16

堆 bss 第 3 页 第 2 页 第 1 页 第 0 页 0

PPN：10 PPN：1 PPN：0 PPN：15 PPN：13 PPN：12 PPN：14 PPN：11 PPN：4

子进程

栈 47

第 5 页 第 4 页 16

堆 bss 第 3 页 第 2 页 第 1 页 第 0 页 0

## 案例 3

```
do_page_fault()
{
    //页面错误虚拟地址
    address = get_page_fault_addr();
    //页面错误的原因
    type = get_page_fault_type();
    //查找地址所属的虚拟内存区域
    vma = find_vma(address);
    if (!vma)
        return fail;

    if (type == WRITE_PROTECT_FAULT)
        do_copy_on_write(); //此处不展开
```

## 案例 4

+   - 以下程序在 Pentium/Linux 上执行。

```
#define PAGE_SIZE 4 * 1024
#define BUF_SIZE 128*PAGE_SIZE

int main(void) {
    char *p = NULL;
    int i;
A: p = mmap(0, 128 * PAGE_SIZE, PROT_READ |
        PROT_WRITE, MAP_PRIVATE | MAP_ANON, 0, 0);
    printf("buffer start: %p\n", p);
    for(i = 0; i < BUF_SIZE; i += PAGE_SIZE)
        p[i] = 1;
B: munmap(p, BUF_SIZE);
    return;
}
```

+   - 当程序执行到标签 A 时，页表如下所示。方框中的数字表示 PDE/PTE 的偏移量。函数 printf 的输出为 `"buffer start: 0xb7bdf000"`。

+   - 当程序执行到标签 B 时，请按照上面的格式写出页表。

+   - 注意：没有数字的白色方框表示空的 PDE/PTE；带数字的白色方框表示已填充的 PDE/PTE；黑色方框表示多个已填充的 PDE/PTE；灰色方框表示包含某些数据/代码的页面。

开始
0xb7bdf000
L1：2DE
L2：3DF

+128K

结束
0xb7c5f000
L1：2DF
L2：05F

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1085_0.png)

## CISC 与 RISC

## Y86

+   - Y86 指令集体系结构
+     - 与 IA32 具有相似的状态和指令
+     - 编码更简单
+     - 介于 CISC 和 RISC 之间

## CISC

+   - 算术指令可以访问内存
+     - addl %eax, 12(%ebx,%ecx,4)
+     - 需要进行内存读写
+     - 复杂的地址计算
+   - 条件码
+     - 作为算术和逻辑指令的副作用被设置

+   - 设计理念
+     - 增加用于执行“典型”编程任务的指令

## RISC

+   - RISC（发音为“risk”）
+   - 设计理念
+     - 针对更简单的指令集形式生成高效代码
+   - 为什么不采用 CISC？
+     - 高级指令很难由编译器生成，而且很少被使用

## 约翰·科克

美国 – 1987 年

## 获奖理由

因其在编译器的设计与理论、大型系统的体系结构以及精简指令集计算机（RISC）的开发方面作出的重大贡献；因发现并系统化了许多如今用于优化编译器的基本转换，包括运算强度削弱、公共子表达式消除、寄存器分配、常量传播和死代码消除。

## 约翰·科克

约翰·科克，又译为约翰·考克、约翰·寇克，生于美国北卡罗来纳州夏洛特，计算机科学家，在电脑架构及编译器最优化技术方面有重大贡献，因此获得图灵奖。曾提出 CYK 算法。在他主导的 IBM 801 计划中，首次采用 RISC 架构，因此被称为 RISC 架构之父。荣誉颇多。

生于：1925 年 5 月 30 日，美国北卡罗来纳州夏洛特（北卡罗来纳州）

逝于：2002 年 7 月 16 日，美国纽约州瓦尔哈拉

教育背景：杜克大学（1953 年），杜克大学（1946 年）

所获奖项：图灵奖，约翰·冯·诺伊曼奖

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1093_0.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_1093_1.png)

## CISC 与 RISC

## CISC

## RISC

用于指定操作数的多种格式。
例如，内存操作数说明符可以由位移量、基址寄存器、变址寄存器和比例因子的多种不同组合构成。

简单的寻址格式。
通常只使用基址加位移量的寻址方式。

