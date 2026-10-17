
## 多级页表

![](img/0d16039e8c3308af077d6d25bb4413a8_253_0.png)

## TLB

- **TLB实际上是操作系统中页表的Cache**
  - TLB主要负责完成用户空间到物理空间的转化
  - 一般与Cache访问同时进行
  - TLB内容：虚地址（Cache的Tag），物理地址（Cache的Data），保护位（Cache的状态）
- **TLB失效处理**
  - TLB失效时需要把相应页表内容从内存取到TLB
  - TLB失效时硬件（如X86的page walker）和软件（如MIPS的特殊例外）来填充TLB

## Cache和虚拟存储

| 比较内容 | Cache | 虚拟存储 |
| --- | --- | --- |
| 调度单位 | 块（16B-128B） | 页（4KB-64KB） |
| 命中延迟 | 1-3时钟周期 | 50-150时钟周期 |
| 失效延迟 | 8-150时钟周期 | 1,000,000-10,000,000时钟周期 |
| 失效率 | 0.1-10% | 0.00001-0.001% |
| 映射前地址 | 25-45位物理地址 | 32-64位虚拟地址 |
| 映射后地址 | 14-20位cache地址 | 25-45位物理地址 |
| 映射者 | 硬件 | 硬件（TLB）+操作系统 |
| 组织方式 | 直接相联、组相联、全相联 | 全相联、组相联（Page Coloring） |
| 替换方式 | 随机、FIFO、LRU | LRU |
| 写回方式 | Write-back、Write-through | Write-back |

## MIPS处理器对虚存系统的支持

## MIPS处理器对虚拟存储的支持

- 分段，段内分页
- TLB
- 特殊的控制寄存器
- 特殊指令
- 专用的例外入口

## MIPS的访问权限

- **User mode**
  - EXL=0 and ERL=0 and KSU=10
- **Supervisor mode**
  - EXL=0 and ERL=0 and KSU=01
- **Kernel mode**
  - EXL=1 or ERL=1 or KSU=00

## MIPS存储空间分段情况

### 32位模式

| 地址范围 | 容量 | 映射方式 | Cached | 访问权限 |
| --- | --- | --- | --- | --- |
| 0xe0000000-0xffffffff | 0.5GB | 查找TLB | Yes (TLB) | Kernel |
| 0xc0000000-0xdfffffff | 0.5GB | 查找TLB | Yes (TLB) | Kernel, Supervisor |
| 0xa0000000-0xbfffffff | 0.5GB | 地址-0xa0000000 | No | Kernel |
| 0x80000000-0x9fffffff | 0.5GB | 地址-0x80000000 | Yes (Config) | Kernel |
| 0x00000000-0x7fffffff | 2GB | 查找TLB | Yes (TLB) | Kernel, Supervisor, User |

## MIPS的TLB及相关控制寄存器

- 32位模式
- 全相联
- 32-64项

**TLB项格式**

| 寄存器/项 | 字段布局 |
| --- | --- |
| 位号 | 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| 位号 | 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| PageMask | 0 / MASK / 0 |
| EntryHi | VPN2 / G / 0 / ASID |
| EntryLo0 | 0 / PFN / C / D / V / 0 |
| EntryLo1 | 0 / PFN / C / D / V / 0 |

**控制寄存器布局**

| 寄存器 | 字段布局 |
| --- | --- |
| 位号 | 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| 位号 | 31 30 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0 |
| PageMask | 0 / MASK / 0 |
| EntryHi | VPN2 / 0 / ASID |
| EntryLo0 | 0 / PFN / C / D / V / G |
| EntryLo1 | 0 / PFN / C / D / V / G |
| Index | P / 0 / Index |
| Random | 0 / Random |
| Wired | 0 / Wired |
| EPC | EPC |
| BadVAddr | Bad Virtual Address |
| Context | PTEBase / BadVPN2 / 0 |

## 与TLB管理有关的指令

- **MFC0, MTC0**
  - 在通用寄存器和控制寄存器之间搬运数据
- **TLBR**
  - 以Index寄存器为索引把TLB内容读到PageMask、EntryHi和EntryLo0/1等寄存器
- **TLBP**
  - 检查EntryHi中指定的虚页是否在TLB中
- **TLBWR, TLBWI**
  - 分别以Random和Index寄存器为索引把PageMask、EntryHi和EntryLo0/1寄存器的内容写入TLB

## TLB例外类型

- **Refill**
  - 如果查找TLB没有找到一个虚地址匹配（VPN2+ASID/G）
  - 例外入口：0x80000000（除非EXL=1）
- **TLB invalid**
  - 如果找到一个虚地址匹配项，但其V=0
  - 例外入口：0x80000180
  - 细分为两种：TLBL for loads, TLBS for stores
- **TLB modify**
  - 如果找到一个虚地址匹配项，其V=1，但D=0且访问为store
  - 例外入口：0x80000180

## 例外返回

- 例外处理器在核心态下进行
  - 不允许在核心态下执行一条用户指令
  - 不允许在用户态下执行内核指令
- 例外返回的两种方式
  - jr+mtc0: mtc0必须在jr的延迟槽中
  - eret: eret没有延迟槽

## 一种虚拟存储实现方式

- 使得发生例外时context寄存器指向页表中相应项
  - 一维线性页表
  - 内存页表每项8个字节，每对页面占用16字节页表
  - 进程切换时操作系统更改context寄存器中PTEBase域，使其指向该进程的页表基地址
- 一维线性页表需要很大的空间，不能全部分配物理内存
  - 放在kernel mapped的kseg2/kseg3段
  - 需要解决TLB refill重入问题

## TLB refill过程

![](img/0d16039e8c3308af077d6d25bb4413a8_266_0.png)

## LINUX操作系统的存储管理

## Linux/MIPS虚拟存储管理

- 虚拟地址空间
- 页表和TLB
  - 页表组织
  - 异常处理函数
  - 一些优化

## Linux/MIPS虚拟地址空间安排

```text
0xFFFFFFFF

mapped(kseg2/3)
内核模块 vmalloc

0xC0000000

Unmapped uncached(kseg1)
Uncached phy mem,
ROM,Register,PCI IO/MEM etc.

0xA0000000

Unmapped cached(kseg0)
内核数据和代码

0x80000000

32-bit user space(kuseg)
(2GB)

0x00000000
```

## 内存中的页表组织（32位情况）

- 两级页表，每项4个字节
  - PFN：物理帧号
  - Flags：V、C、D
  - Exts：软件扩展位，用于维护一些硬件没有实现的功能，例如ref位，modified位
- 页表存放在kseg0
  - 页表访问不引起TLB例外
  - 页表存储空间在使用到的时候分配
- 每个进程的页表基地址存放在进程上下文中
