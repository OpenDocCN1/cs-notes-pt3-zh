

## Pentium 分段
- 允许一个段最大为 4GB，每个进程的最大段数为 16K(=16384)。
- 进程的逻辑地址空间被划分为两个分区
  - 1st, 最多 8K 段，私有给该进程
  - 2nd, 最多 8K 段，供所有进程共享
- 第 1 个分区的信息保存在局部描述符表 LDT 中；第 2 个分区的信息保存在全局描述符表 GDT 中。
- LDT 和 GDT 中的每个条目都由一个 8 字节的段描述符组成，其中包含有关特定段的详细信息，包括该段的基地址和界限。

## Pentium 分段
- **逻辑地址：(选择子, 偏移量)**
  - 选择子是一个 16 位数字，**13 位 s，1 位 g，和 2 位 p**
    - s，段号
    - g，段是否在 GDT 或 LDT 中
    - p，处理保护
  - offset，32 位数字，段内字节的位置
- 该机器有六个段寄存器，允许进程在任何时候寻址 6 个段。
- 它有六个 8 字节微程序寄存器，用于保存来自 LDT 或 GDT 的相应描述符。 (cache)

## Pentium 分段
- 段寄存器指向 LDT 或 GDT 中的适当条目。
- 基地址和界限信息用于生成线性地址。

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_575_0.png)

## Pentium 分页
- 允许页面大小为 4KB 或 4MB
- 对于 4KB 页面，Pentium 使用两级分页方案。
- 线性地址：32 位长
  - 20 位页号
    - 10 位页目录指针 (P1)
    - 10 位页表指针 (P2)
  - 12 位偏移量 (d)

| page number | page offset |
|---|---|
| P₁ | P₂ | d |

## Pentium 分页
- **页目录中的一个条目是页大小标志，**
  - 如果设置，页面大小为 4MB
  - 如果未设置，页面大小为 4KB
- **对于 4MB 页面大小**
  - 页目录直接指向 4-MB 页帧
  - 线性地址中的 22 个低位表示 4-MB 页帧内的偏移量。

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_578_0.png)

## Pentium 分页
- **页表可以交换到磁盘**
  - 使用一个无效位
  - 如果已交换，操作系统使用其他 31 位来指定表的磁盘位置

## 地址转换

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_580_0.png)

logical address

segment | g | p | offset

descriptor table

limit | base

linear address

directory | page | offset

page directory

page table base

page table

frame number

page frame

physical address

page directory base register

## Linux on Pentium systems
- 仅提供对分段的有限支持
- Linux 不依赖于分段并最小化使用它。
- 在 Pentium 上，Linux 仅使用六个段：
  - 一个内核代码段
  - 一个内核数据段
  - 一个用户代码段
  - 一个用户数据段
  - 一个任务状态段 (TSS)
  - 一个默认 LDT 段

shared by all processes running in user mode

Used to store the hardware context of each process during context switches.

Is normally shared by all processes and is usually not used

## Linux 中的三级分页

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_583_0.png)

## 作业 (第 310 页)
- 8.3
- 8.5
- 8.9
- 8.12

## 思考：
- 8.1
- 8.10
- 8.11
- 8.13

## 补充：

## 关于主存管理

## 内存管理的目标
- 将内存细分以容纳多个进程
- 内存需要被有效分配以尽可能多地将进程打包到内存中

## 补充：
## 内存管理需求 (1/5)

## 重定位
- 程序员在程序执行时并不知道程序将在内存中的何处放置
- 程序执行时，它可能被交换到磁盘并返回到主存的不同位置 (重定位)
- 内存引用必须在代码中被转换为主物理内存地址

