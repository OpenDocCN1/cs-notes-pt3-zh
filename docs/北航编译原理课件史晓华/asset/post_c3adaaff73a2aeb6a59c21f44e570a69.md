
## 12.1.2 存贮层次结构

寄存器、缓存、内存、硬盘的存储访问特性

| Level | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| Called | Registers | Cache | Main memory | Disk storage |
| Typical size | < 1 KB | < 16 MB | < 16 GB | > 100 GB |
| Implementation technology | Custom memory with multiple ports, CMOS | On-chip or off-chip CMOS SRAM | CMOS DRAM | Magnetic disk |
| Access time (in ns) | 0.25–0.5 | 0.5 to 25 | 80–250 | 5,000,000 |
| Bandwidth (in MB/sec) | 20,000–100,000 | 5,000–10,000 | 1,000–5,000 | 20–150 |
| Managed by | Compiler | Hardware | Operating system | Operating system/operator |
| Backed by | Cache | Main memory | Disk | CD or Tape |

![](img/1ebd4dbc150db02388404d0c659c1fd7_738_0.png)

## 虚拟内存、物理内存和磁盘

![](img/1ebd4dbc150db02388404d0c659c1fd7_739_0.png)

## 1980～2000年，CPU性能和内存访问性能的提高

![](img/1ebd4dbc150db02388404d0c659c1fd7_740_0.png)

## 通过循环交换（Loop Interchange）优化提高缓存命中率

```
for (j = 0; j < 100; j = j+1)
    for (i = 0; i < 5000; i = i+1)
        x[i][j] = 2 * x[i][j];
```

**x[0][0]**, x[0][1], …, x[0][99], **x[1][0]**, x[1][1], …, x[1][99], …, **x[4999][0]**, x[4999][1], …, x[4999][99]

```
for (i = 0; i < 5000; i = i+1)
    for (j = 0; j < 100; j = j+1)
        x[i][j] = 2 * x[i][j];
```

**x[0][0]**, x[0][1], …, x[0][99], x[1][0], x[1][1], …, x[1][99], …, x[4999][0], x[4999][1], …, x[4999][99]

## 提高数据局部性!

```
/* Before */
for (i = 0; i < N; i = i+1)
    for (j = 0; j < N; j = j+1)
    {
        r = 0;
        for (k = 0; k < N; k = k + 1)
            r = r + y[i][k] * z[k][j];
        x[i][j] = r;
    }
```

![](img/1ebd4dbc150db02388404d0c659c1fd7_742_0.png)

```
/* After */
for (jj = 0; jj < N; jj = jj+B)
for (kk = 0; kk < N; kk = kk+B)
for (i = 0; i < N; i = i+1)
    for (j = jj; j < min(jj+B,N); j = j+1)
    {
        r = 0;
        for (k = kk; k < min(kk+B,N); k = k + 1)
            r = r + y[i][k] * z[k][j];
        x[i][j] = x[i][j] + r;
    }
```

![](img/1ebd4dbc150db02388404d0c659c1fd7_742_1.png)

## 12.1.3 流水线

## XScale core RISC 超流水线

![](img/1ebd4dbc150db02388404d0c659c1fd7_743_0.png)

| 指令 | 延迟 |
|---|---:|
| $I0$: `add R0, R5, R6` | 1 |
| $I1$: `sub R1, R7, R8` | 1 |
| $I2$: `ldr R2, [R4, 0x47]` | 3 |
| $I3$: `add R3, R2, R1` | 1 |

时钟周期：$1+1+3+1=6$

| 指令 | 延迟 |
|---|---:|
| $I2$: `ldr R2, [R4, 0x47]` | 3* |
| $I0$: `add R0, R5, R6` | 1 |
| $I1$: `sub R1, R7, R8` | 1 |
| $I3$: `add R3, R2, R1` | 1 |

时钟周期：$1+1+1+1=4$

- Multiple-issued processor
  - Intel PIII/P4
- Very Long Instruction Word (VLIW)
  - i860
- Explicitly Parallel Instruction Computers (EPIC)
  - IA64

## A centralized shared-memory multiprocessor

![](img/1ebd4dbc150db02388404d0c659c1fd7_746_0.png)

线程级并行!

## Distributed-memory multiprocessors

![](img/1ebd4dbc150db02388404d0c659c1fd7_746_1.png)

## 数据级并行！

- 多核协处理器
  - GPU, GPGPU
- 异构CMP
  - 同构CMP + 多核协处理器

![](img/1ebd4dbc150db02388404d0c659c1fd7_747_0.png)

![](img/1ebd4dbc150db02388404d0c659c1fd7_747_1.png)

ATI Radeon x1900拥有48个Pixel Shader处理器，每个都可以在1个时钟周期内处理4个浮点运算。性能达到250 GFLOPS。

## 在100个处理器上想要达到80倍的加速比，串行部分的运行只能占原计算的0.25%！

Amdahl's Law is

```
Speedup = 1 / ( Fraction_enhanced / Speedup_enhanced + (1 - Fraction_enhanced) )
```

```
80 = 1 / ( Fraction_parallel / 100 + (1 - Fraction_parallel) )
```

Simplifying this equation yields

```
0.8 × Fraction_parallel + 80 × (1 - Fraction_parallel) = 1
```

```
80 - 79.2 × Fraction_parallel = 1
```

```
Fraction_parallel = (80 - 1) / 79.2
```

```
Fraction_parallel = 0.9975
```

## 12.2.1 程序地址空间的实例分析

```
// C12P1.cpp
#include "stdafx.h"
int global_val = 0;
int foo(int n){
    static int static_val = 0;
    int i;
    for(i=0; i<100; i++){
        n = n * i + global_val + static_val;
    }
    static_val = n / 2;
    printf("static_val is %x\n", static_val);
    return n;
}
int main(int argc, char* argv){
    global_val = 99;
    int n = foo(100);
    printf("foo(100) is %x\n",n);
    return 0;
}
```

```
1       TITLE           C12P1.cpp
2       .386P
3       .model FLAT
4
5       PUBLIC              ?global_val@@3HA
                        :global_val
6       BSS                 SEGMENT
7       ?global_val@@3HA DD 01H DUP (?)
                        :global_val
8       BSS                 ENDS
9
10      PUBLIC              ?foo@@YAHH@Z
                        :foo
11      PUBLIC              ??_C@_0BC@BPOF@static_val?5is?5%SCFd?6SAA@
                        :string
12      EXTRN              printf:NEAR
13      DATA                SEGMENT
14      ??_C@_0BC@BPOF@static_val?5is?5%SCFd?6SAA@ DB 'static_val is %x', 0aH,
00H, 'string'
15      DATA                ENDS
16      _TEXT                SEGMENT
17      _t$8 = 8
18      ?foo@@YAHH@Z PROC NEAR
                        :foo
19      ... foo的函数体省略
20      ?foo@@YAHH@Z ENDP
                        :foo
21      _TEXT                ENDS
22
23      PUBLIC              __main
24      4                   P   U   B   L   I   C
25      ??_C@_0BA@OOBN?g?foo?5C100?5C?5is?5%SCFd?6%SAA@ DB 'string'
26      _DATA                SEGMENT
27      ??_C@_0BA@OOBN?g?foo?5C100?5C?5is?5%SCFd?6SAA@ DB 'foo(100) is %x',
0aH, 00H; 'string'
28      _DATA                ENDS
29      _TEXT                SEGMENT
30      _main                PROC NEAR
31      ... _main的函数体省略
32      _main                ENDP
33      _TEXT                ENDS
END
```
