
## Paging Hardware With TLB

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_539_0.png)

## Implementation of Page Table

- Some TLBs store **address-space identifiers (ASIDs)** in each TLB entry – uniquely identifies each process to provide address-space protection for that process.
- ASID allows the TLB to contain entries for several different processes simultaneously. Otherwise it need to be flushed at every context switch.

## Effective Access Time

- **Hit ratio (命中率)** – percentage of times that a page number is found in TLB.
- Hit ratio = α
- TLB Lookup = ε time unit
- Assume memory cycle time is 1 microsecond
- Effective Access Time (EAT)

EAT = (1 + ε) α + (2 + ε)(1 − α)

= 2 + ε − α

## Exercise3

考虑一个分页系统，其页表存放在内存：

- （1）如果内存读写周期为2μ s，则CPU从内存取一条指令或一个操作数需要时间为多少？

- （2）如果设立一个可存放8个页表项的TLB，70%的地址变换可通过TLB完成，内存平均存取时间为多少？（假设TLB的访问时间可以忽略不计）

## Memory Protection

- Memory protection implemented by associating protection bit with each frame in a paged environment.
- *Valid-invalid bit* attached to each entry in the page table:
  - “valid” indicates that the associated page is in the process’s logical address space, and is thus a legal page.
  - “invalid” indicates that the page is not in the process’s logical address space.

## Valid (v) or Invalid (i) Bit In A Page Table

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_544_0.png)

| Page table entry | Frame number | Valid-invalid bit |
|---:|---:|:---:|
| 0 | 2 | v |
| 1 | 3 | v |
| 2 | 4 | v |
| 3 | 7 | v |
| 4 | 8 | v |
| 5 | 9 | v |
| 6 | 0 | i |
| 7 | 0 | i |

## Memory Protection

- we can use a *page table length register* *(PTLR)* that stores the length of a process’s page table. In this way, a process cannot access the memory beyond its region.
- We can also add read-only, read-write, or execute bits in page table to enforce r-w-e permission.

## Shared Pages

- Shared code: One copy of **read-only (reentrant)** code shared among processes (i.e., text editors, compilers, window systems).
- Each process keeps a separate copy of the private code and data

## Outline

- Background
- Contiguous Allocation
- Paging
- Structure of Page Table
- Segmentation

## Structure of Page Table

- Hierarchical Paging
- Hashed Page Tables
- Inverted Page Tables

## Hierarchical Paging

- Break up the logical address space into multiple page tables.
- A simple technique is a two-level page table.

## Two-Level Paging Example

- A logical address (on 32-bit machine with 4K page size) is divided into:
  - a page number consisting of 20 bits.
  - a page offset consisting of 12 bits.
- Since the page table is paged, the page number is further divided into:
  - a 10-bit page number.
  - a 10-bit page offset.

## Two-Level Paging Example

Thus, a logical address is as follows:

| page number | page offset |
|---|---|
| p₁ | p₂ | d |

10 10 12

where p₁ is an index into the outer page table, and p₂ is the displacement within the page of the outer page table.

## Two-Level Page-Table Scheme

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_553_0.png)

## Three-level Paging Scheme

| outer page | inner page | offset |
|---|---|---|
| $p_1$ | $p_2$ | $d$ |
| 42 | 10 | 12 |

| 2nd outer page | outer page | inner page | offset |
|---|---|---|---|
| $p_1$ | $p_2$ | $p_3$ | $d$ |
| 32 | 10 | 10 | 12 |

## Exercise4

- 某计算机采用二级页表的分页存储管理方式，按字节编址，页大小为 $2^{10}$B，页表项大小为2B，逻辑地址结构为（页目录号，页号，页内偏移量），逻辑地址空间大小为 $2^{16}$ 页，则表示整个逻辑地址空间的页目录表中包含表项的个数至少是多少？

## Hashed Page Tables

- Common in address spaces > 32 bits.
- The virtual page number is hashed into a page table. Each entry in this page table contains a chain of elements hashing to the same location.
- Virtual page numbers are compared in this chain searching for a match. If a match is found, the corresponding physical frame is extracted.
