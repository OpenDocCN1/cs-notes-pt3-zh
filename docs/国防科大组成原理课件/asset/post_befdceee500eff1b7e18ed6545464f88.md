
## Linux/MIPS的两层页表

![](img/0d16039e8c3308af077d6d25bb4413a8_272_0.png)

## Linux的tlb重填代码（共18条指令）

```
mfc0 k0, CP0_BADVADDR
srl  k0, k0, 22
lw   k1, pgd_current
sll  k0, k0, 2
addu k1, k1, k0
mfc0 k0, CP0_CONTEXT
lw   k1, (k1)
srl  k0, k0, 1
and  k0, k0, 0xff8
addu k1, k1, k0
lw   k0, 0(k1)
lw   k1, 4(k1)
srl  k0, k0, 6
mtc0 k0, CP0_ENTRYLO0
srl  k1, k1, 6
mtc0 k1, CP0_ENTRYLO1
tlbwr	eret
```

# 取发生tlb miss的地址
# 最高10位是第一级页表的索引
# 取页表入口指针
# 每项4个字节，所以索引*4=偏移
# *k1指向下一级页表入口
#context包含失效的虚页号
# 取出第二级页表
# 算出第二级页表的偏移
# 成对存放，一个偶数页
# 加一个奇数页
# 移出6位软件作用的位
# 写入偶数页表项
# 写入奇数页表项
# 写入TLB的一个随机项
# 异常返回

## 例子

- **Array=(int*)malloc(0x1000)**
  - 用户程序malloc(0x1000)返回虚地址0x450000
  - 操作系统在该进程的vma_struct链表中记录地址范围0x450000-0x4501000为已分配地址，可读可写
- **For (I=0;I<1024;I++) Array[i] = 0**
  - 用户程序试图写0x450000，TLB查找失败，引起tlb refill例外
  - Tlb refill从相应页表位置取入页表内容填入TLB。但该页表还没初始化
  - 例外返回到用户程序，重新开始访问
  - TLB表项找到，但是无效，发生TLB Invalid例外
  - 操作系统查找vma_struct，判断该地址已分配，处于可写状态，因此为它分配物理页面，并将物理地址填入页表，更新TLB
  - 例外返回，写操作再次重试，成功。
  - 用户程序继续写0x450004,008..., 因为TLB页已经存在，将全速运行，除非中间发生进程切换导致其TLB项被换出。如果发生被换出的情况，再次运行时将会发生refill例外从页表取得有效内容，不会再发生invalid例外(因此,refill频率>>invalid)
  - 为什么要分成两次例外？

## Linux/MIPS中TLB例外的处理

- tlb refill exception(0x80000000):
  (1) get badaddr,pgd
  (2) pte table ptr = badaddr>>22 < 2 + pgd ,
  (3) get context, offset = context >> 1 & 0xff8 (bit 21-13 + three zero),
  (4) load offset(pte table ptr) and offset+4(pte table ptr),
  *(5) right shift 6 bits,write to entrylo[01],
  (6) tlbwr
- tlb modified exception(handle_mod):
  (1) load pte,
  *(2) if _PAGE_WRITE set,set ACCESSED | MODIFIED | VALID | DIRTY,
      reload tlb,tlbwi
      else DO_FAULT(1)
- tlb load exception(handle_tlbl):
  (1) load pte
  (2) if _PAGE_PRESENT && _PAGE_READ, set ACCESSED | VALID
      else DO_FAULT(0)
- tlb store exception(handle_tlbs):
  (1) load pte
  *(2) if _PAGE_PRESENT && _PAGE_WRITE,set ACCESSED | MODIFIED | VALID | DIRTY
      else DO_FAULT(1)

## TLB性能分析和一些优化

- 一些数据
- 优化思路

## TLB相关性能数据

- • TLB miss处理的时间可以占到高达40%的运行时间，
  占40~90%的内核运行时间

- • SPEC2000里大约1/4的程序有比较显著的TLB miss

- • 目前多数处理器的TLB是全相连的32-128项，如果每项4k，能映射的空间只有几百K，越来越难满足现代程序的需求

## 优化的思路

- 增加**TLB**的大小（两级TLB）
- 提高**TLB**覆盖空间的大小（多页支持）
- 提高**TLB**异常处理的效率（软TLB等缓存技术）

## 增加页大小后性能显著提高

- 增加页大小后，TLB失效明显减少
- 16KB页时128页有2MB

![](img/0d16039e8c3308af077d6d25bb4413a8_280_0.png)

![](img/0d16039e8c3308af077d6d25bb4413a8_280_1.png)

## 软TLB的方案

- 目的：主要减少TLB重载入异常处理的时间，提高TLB重载入异常处理的效率。
- 原理：通过减少TLB重载入异常处理过程Cache Miss的次数来减少TLB重载入异常处理的时间

## 软TLB的方案（续）

![](img/0d16039e8c3308af077d6d25bb4413a8_282_0.png)

## 软TLB的命中率

软TLB在ref规模下的命中率（4K的软TLB表项，直接映射）

![](img/0d16039e8c3308af077d6d25bb4413a8_283_0.png)

## 缓冲区大小对软TLB命中率的影响

## 软TLB大小对命中率的影响

![](img/0d16039e8c3308af077d6d25bb4413a8_284_0.png)

## 软TLB对SPEC性能的提高

软TLB对SPEC2000在ref规模下分数的提高

![](img/0d16039e8c3308af077d6d25bb4413a8_285_0.png)

## 利用TLB的保护机制防范攻击

- 利用缓冲区溢出进行攻击的例子
- 龙芯处理器通过可执行保护防止缓冲区溢出攻击
- TLB增加可执行位

```
void fa(void) {
    ...
    function fb(str);
    ...
}

void fb(char *str) {
    ...
    char buffer[16];
    ...
    gets(buffer);
    ...
}
```

![](img/0d16039e8c3308af077d6d25bb4413a8_286_0.png)

## 常见处理器的结构参数

|  |  | Intel Ivybridge | AMD BullDozer | IBM Power7 | GS464E |
|---|---|---|---|---|---|
|  | 一级指令缓存 | 32KB, 8 路, 64B/行 | 64KB, 2路, 64B/行 | 32KB, 4 路, 128B/行 | 64KB, 4 路, 64B/行 |
| 前端 | 指令TLB | 128 项, 4 路, L1 ITLB | 72 项, 全相联, L1 ITLB
512 项, 4 路, L2 ITLB | 64 项, 2 路, L1 ITLB | 64 项, 全相联, L1 ITLB |
|  | 分支预取 | BTB (8K-16K?项)
间接目标队列 (? 项)
RAS (? 项)
循环检测 | 512 项, 4 路 L1 BTB
5120 项, 5 路 L2 BTB
512 项 间接目标队列
24 项 RAS
循环检测 | 8K 项本地 BHT 队列,
16K 项全局BHT 队列,
8K 项 全局 sel 队列
128 项间接目标队列
16 项 RAS | 8K项本地 BHT 队列
8K项全局BHT 队列
8K项 全局 sel 队列
1K项间接目标队列
16 项 RAS
循环检测 |
| 乱序执行 | ROB | 168 项 | 128 项 | 120 项 | 128 项 |
|  | 发射队列 | 54-项 统一 | 60-项 浮点(共享)
40-项 定点, 访存 | 48-项 标准 | 24-项 浮点;
16-项 定点;
32-项 访存 |
|  | 寄存器重命名 | 160 定点;
144 浮点 | 96 定点;
160 浮点(双核共享) | 80 定点,浮点;
56 CR;
40 XER,
24 Link&Count | 128 定点;
128 浮点/向量;
16 Acc;
32 DSPCtrl; 32 FCR |
| 运算部件 | 执行单元 | ALU/LEA/Shift/128位 MUL/128位 Shift/256位FMUL/256位 Blend +
ALU/LEA/Shift/128位 ALU /128位 Shuffle/256位 FADD +
ALU/Shift/Branch/128位 ALU/128bit Shuffle/256位 Shuffle/256位 Blend | ALU/IMUL/Branch +
ALU/IDIV/Count +
128位FMAC/128位 IMAC +
128位FMAC/128位 XBAR +
128位 MMX +
128位 MMX/128位 FSTO | 2 定点 +
2 浮点/向量 +
1 转移 +
1 CR | 2 定点/转移/DSP +
2 浮点/向量 |
|  | 向量宽度 | 256位 | 128位 | 128位 | 256位 |
