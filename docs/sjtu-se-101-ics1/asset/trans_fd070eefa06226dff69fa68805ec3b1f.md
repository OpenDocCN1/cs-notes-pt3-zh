

## 寻找空闲块

- First fit:
  - 从开头搜索列表，选择第一个合适的空闲块
  - 在总块数（已分配和空闲）上可能需要线性时间
  - 实际上它可能导致列表开头出现“碎片”

## 寻找空闲块

- Next fit:
  - 类似 first-fit，但从上一次搜索结束的位置开始搜索列表
  - 研究表明碎片化更严重
- Best fit:
  - 搜索列表，选择大小最接近且合适的空闲块
  - 保持碎片小——通常有助于碎片化
  - 通常比 first-fit 运行更慢

## 在空闲块中分配

- 在空闲块中分配 - *拆分*
  - 由于已分配空间可能小于空闲空间，我们可能希望拆分该块

![](img/b3f8b91675c485f1e811aa092ebbf3d4_961_0.png)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_961_1.png)

## 释放块

- 最简单的实现：
  - 只需清除已分配标志
  - 但可能导致“假碎片化”
  - 有足够的空闲空间，但分配器无法找到它

free(p)

malloc(5)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_962_0.png)

## 合并

- 如果相邻的下一个和/或上一个块是空闲的，则合并它们
  - 与下一个块合并
  - 但我们如何与上一个块合并？

free(p)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_963_0.png)

## 双向

- 边界标签 [Knuth73]
  - 在空闲块底部复制 size/allocated 词
  - 允许我们向后遍历“列表”，但需要额外空间
  - 重要且通用的技术！

## 双向

已分配块和空闲块的格式

![](img/b3f8b91675c485f1e811aa092ebbf3d4_965_0.png)

1 word

header

boundary tag (footer)

a = 1: allocated block
a = 0: free block

size: block size

payload: application data
(allocated blocks only)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_965_1.png)

## 常数时间合并

![](img/b3f8b91675c485f1e811aa092ebbf3d4_966_0.png)

## 常数时间合并 (case 1)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_967_0.png)

## 常数时间合并 (case 2)

| m1 | 1 |
|---|---|
|   |   |
| m1 | 1 |
| n | 1 |
|   |   |
| n | 1 |
| m2 | 0 |
|   |   |
| m2 | 0 |

![](img/b3f8b91675c485f1e811aa092ebbf3d4_968_0.png)

| m1 | 1 |
|---|---|
|   |   |
| m1 | 1 |
| n+m2 | 0 |
|   |   |
|   |   |
|   |   |
| n+m2 | 0 |

## 常数时间合并 (case 3)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_969_0.png)

## 常数时间合并 (case 4)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_970_0.png)

## 动态内存分配

## 大纲

- The allocation functions
- Suggested reading: 9.9

## 动态内存分配

- Explicit vs. Implicit Memory Allocator
  - Explicit: application allocates and frees space
    - E.g., `malloc` and `free` in C
  - Implicit: application allocates, but does not free space
    - E.g. garbage collection in Java, ML or Lisp

## 动态内存分配

- Allocation
  - 在这两种情况下，内存分配器都将内存抽象为一组块
  - 将空闲内存块分配给应用程序

Kernel virtual memory

Memory invisible to user code

User stack
(created at run time)

Memory mapped region for shared libraries

printf function

Run-time heap (created at run time by malloc)

Read/write data

Read-only code and data

0x08048000 (32)

0x00400000 (64)

0

Loaded from the hello executable file

## Malloc package

- `#include <stdlib.h>`
- `void *malloc(size_t size)`
  - if successful:
    - returns a pointer to a memory block of at least size bytes, aligned to 8-byte boundary.
    - if size==0, returns NULL
  - if unsuccessful: returns NULL
- `void free(void *p)`
  - returns the block pointed at by p to pool of available memory
  - p must come from a previous call to malloc,calloc or realloc.

