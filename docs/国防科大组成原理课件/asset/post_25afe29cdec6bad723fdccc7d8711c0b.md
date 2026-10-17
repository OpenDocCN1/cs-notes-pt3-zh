
## TLB初始化

- **TLB用于虚实地址转换**
- 从TLB来看，MIPS地址空间，分为非映射与映射
  - 0x80000000 – 0x8FFFFFFF: Cached/Unmapped内存空间
  - 0x9FC00000 – 0x9FCFFFFF: Cached/Unmapped取指空间
  - 0xB0000000 – 0xBFFFFFFF: Uncached/Unmapped IO空间
  - 对于BIOS，基本使用非映射空间，无需TLB转换
- 对于大地址空间的使用，会借助TLB映射
  - 0xC0000000 -> 0x40000000: 对应显存等大IO空间

## TLB初始化代码

- 逐一清空每一个TLB项
  - 需要使用时再填入正确映射（通过TLB Refill例外）

```
LEAF(CPU_TLBclear)
    li      a3, 0
    li      a2, 64
    li      a2, PG_SIZE_4K
    MTCO    a2, COP_0_TLB_PG_MASK
1:
    MTCO    zero, COP_0_TLB_HI    对TLB_HI寄存器初始化，对应于VPN
    MTCO    zero, COP_0_TLB_LO0   对TLB_LO0寄存器初始化，对应于PFN0
    MTCO    zero, COP_0_TLB_LO1   对TLB_LO1寄存器初始化，对应于PFN1
    mtc0    a3, COP_0_TLB_INDEX    当前处理的TLB项索引号
    addiu   a3, 1
    tlbwi                   操作TLB表
    bne     a3, a2, 1b
    nop
    jr      ra
    nop
END(CPU_TLBclear)
```

## Cache初始化

- 复位后BIOS刚开始启动时，处理器从非缓存空间开始执行
  - 上百拍完成一条指令的的取指和执行
  - Cache初始化后，跳转到Cache空间执行，全速流水
  - 尽早完成Cache初始化，使用Cache地址执行能够大大提升启动速度
- 从Cache来看，MIPS地址空间，分为非缓存与缓存
  - 0x80000000 – 0x8FFFFFFF: Cached/Unmapped内存空间
  - 0x9FC00000 – 0x9FCFFFFF: Cached/Unmapped取指空间
  - 0xB0000000 – 0xBFFFFFFF: Uncached/Unmapped IO空间
  - Cached/Unmapped取指空间和Uncached/Unmapped IO空间的物理地址是相同的，Cache失效会自动到IO空间去取指

## 一级Cache初始化代码

```
```assembly
LEAF(godson2_cache_init)
    lui     a0, 0x8000
    li      a2, (1<<14)

    mtc0    $0, CP0_TAGHI
    mtc0    $0, CP0_TAGLO
    li      a1, 0x22
    addiu   v0, $0, a0
    addu    v1, a0, a2

1:
    slt     a3, v0, v1
    beq     a3, $0, 2f
    nop
    mtc0    a1, CP0_ECC
    cache   Index_Store_Tag_D, 0x0(v0)
    cache   Index_Store_Tag_D, 0x1(v0)
    cache   Index_Store_Tag_D, 0x2(v0)
    cache   Index_Store_Tag_D, 0x3(v0)
    mtc0    zero, CP0_ECC
    cache   Index_Store_Tag_I, 0x0(v0)
    cache   Index_Store_Tag_I, 0x1(v0)
    cache   Index_Store_Tag_I, 0x2(v0)
    cache   Index_Store_Tag_I, 0x3(v0)
    b       1b
    daddiu  v0, v0, 0x20

2:
    jr      ra
    nop
END(godson2_cache_init)
```
```

基地址
64KB/4路，为Index的实际数量

对TAGHI进行初始化
对TAGLO进行初始化
A1寄存器用于存放ECC校验码，全0时，ECC位为0x22

根据V0和V1的值判断是否已经完成所有项的遍历

数据Cache采用ECC校验，初始化为0x22

对4路数据Cache分别进行写TAG操作

指令Cache采用奇偶校验，初始化为0

对4路指令Cache分别进行写TAG操作

## 开Cache执行

- Cache初始化仅仅是使Cache可用
- 要使用Cache必须开Cache，并使用Cache地址操作
- 注意0xA0000000段和0x80000000段的物理地址是相同的

```
## enable kseg0 cachability##
    mfc0    t6, CP0_CONFIG
    ori     t6, t6, 7
    xori    t6, t6, 4
    mtc0    t6, CP0_CONFIG

#jump to cached kseg0 address
PRINTSTR("Jump to 9fc\r\n")
    lui     t0, 0x9f
    ori     t0, t0, 0xffff
    bal     1f
    nop
1:
    and     ra, ra, t0
    addiu   ra, ra, 16
    jr      ra
    nop
2:

开Cache执行
使能0x80000000 - 0x9FFFFFFF的Cache功能

将程序地址跳转到0x9FC0000段执行
BIOS执行到该位置时, 应该在Uncache的取指执行,
所在的地址段为0xBFC00000 - 0xBFCFFFFF.

BAL指令将会将延迟槽后的指令地址填入RA寄存器,
正常情况下为0xBFCxxxxx.

0xBFCx & 0xDFFF = 0x9FCx, 地址变换为Cached
将记录的地址再加16, 实际上是原指令后的第4条, 也
即标号2处的指令
跳转到该指令的Cache空间处
```

## Cache算法配置

- 三位决定Cache算法
  - 对于kseg0段（0x80000000段），由Config寄存器的k0域决定
  - 其它部分由TLB表项决定
  - 2、3分别表示uncached和cached，其余6个值自定义

![](img/0d16039e8c3308af077d6d25bb4413a8_419_0.png)

## 提纲

- 处理器核初始化
- 总线接口初始化
- 设备探测及驱动加载
- 多核启动过程

## 内存控制器配置代码

- 将预先定义好的值写入内存控制器的相应寄存器中
- 内存控制器将自动对内存进行初始化配置
  - 主要设置延迟、匹配阻抗等
- 初始配置之后，会再对内存信号进行训练

```
ddr2_config:
    caddiu    a2, a2, s0
    dli       t1, DDR_PARAM_NUM
    caddiu    v0, c8, 0x0
1:
    ld        a1, 0x0(a2)
    sd        a1, 0x0(v0)
    caddiu    t1, t1, -1
    caddiu    a2, a2, 0x8
    caddiu    v0, v0, 0x8
    bnez      t1, 1b
    nop
```

a2为调用该程序时传入的参数，与s0之间用于表示初始化参数在FLASH中的基地址
t1用于表示内存参数的个数
t8为调用该程序时传入的参数，用于表示内存控制器的寄存器基地址
初始化的过程就是从FLASH中取数再写入内存控制器中的寄存器的过程

## IO总线初始化

- 根据不同IO总线的需求进行针对性的初始化
- 通过初始化配置消除与具体实现相关的总线特性，保证软件兼容性
  - 信号定义，硬件实现各不相同： HyperTransport、 PCIE等
  - 软件协议兼容PCI： 配置空间、 IO空间及Memory空间
- 龙芯3号中使用HyperTransport接口
  - 地址划分： 确定配置访问、 IO访问及Memory访问的地址
  - 设定DMA访问地址
  - 对总线频率、宽度进行重新设置
