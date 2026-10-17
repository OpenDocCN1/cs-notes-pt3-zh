
## EEMBC – 动态指令分布

![](img/0d16039e8c3308af077d6d25bb4413a8_778_0.png)

## 并行系统基准测试程序

- 多核、多处理器等并行系统，和单线程系统不同的是其存在着并行性的瓶颈
  - 多个线程之间共享资源的竞争
  - 算法中数据相互依赖等。
- 并行基准测试程序用于测试和评价并行系统的性能
  - **SPLASH-2**：测并行加速比
  - **PARSEC**：测并行加速比
  - **NPB**：测并行加速比
  - **LINPACK**：测并行浮点峰值

## SPLASH-2

- 斯坦福大学95年推出的并行程序SPLASH（Stanford Parallel Applications for Shared Memory）
  - 12个程序组成，4个核心程序和8个应用，使用Pthread 并行编程模式

| Program | Application Domain | Problem Size |
|---|---|---|
| barnes | High-Performance Computing | 65,536 particles |
| cholesky | High-Performance Computing | tk29.O |
| fft | Signal Processing | 4,194,304 data points |
| fmm | High-Performance Computing | 65,536 particles |
| lu | High-Performance Computing | 1024 × 1024 matrix, 64 × 64 blocks |
| ocean | High-Performance Computing | 514 × 514 grid |
| radiosity | Graphics | large room |
| radix | General | 8,388,608 integers |
| raytrace | Graphics | car |
| volrend | Graphics | head |
| water | High-Performance Computing | 4096 molecules |

## PARSEC-3.0

- 普林斯顿大学2009年推出了PARSEC（The Princeton Application Repository for Shared-Memory Computers）
- 面向新兴应用，评价多核和多处理器系统，包括金融计算、计算机视觉、物理建模、未来媒体、搜索和重复数据删除

表 16.7 PARSEC 并行测试程序集

| 程序 | 应用领域 | 并行模式 | 并行粒度 | 数据共享 | 数据交换 | Pthreads | OpenMP | TBB |
|---|---|---|---|---|---|---|---|---|
| blackscholes | 金融分析 | 数据并行 | 粗粒度 | 低 | 低 | X | X | X |
| bodytrack | 计算机视觉 | 数据并行 | 中等粒度 | 高 | 中等 | X | X | X |
| canneal | 工程类 | 非结构化 | 细粒度 | 高 | 高 | X |  |  |
| dedup | 企业存储 | 流水线 | 中等粒度 | 高 | 高 | X |  |  |
| facesim | 动画 | 数据并行 | 粗粒度 | 低 | 中等 | X |  |  |
| ferret | 相似性查找 | 流水线 | 中等粒度 | 高 | 高 | X |  |  |
| fluidanimate | 动画 | 数据并行 | 细粒度 | 低 | 中等 | X |  | X |
| freqmine | 数据挖掘 | 数据并行 | 中等粒度 | 高 | 中等 |  | X |  |
| raytrace | 渲染 | 数据并行 | 中等粒度 | 高 | 低 | X |  |  |
| streamcluster | 数据挖掘 | 数据并行 | 中等粒度 | 低 | 中等 | X |  | X |
| swaptions | 金融分析 | 数据并行 | 粗粒度 | 低 | 低 | X |  | X |
| vips | 媒体处理 | 数据并行 | 粗粒度 | 低 | 中等 | X |  |  |
| x264 | 媒体处理 | 流水线 | 粗粒度 | 高 | 高 | X |  |  |

## NPB-3.3

- NPB（NAS Parallel Benchmark）是美国国家航空航天局开发流体动力学计算的应用程序集，用于评测大规模并行机
- 包括OpenMP和MPI等版本
- 包括5个核心程序和3个模拟应用。每个程序有5类问题规模，分别为A、B、C、S和W

Table 1: Standard operation counts for the NPB.

| Benchmark Name | Abb. | Class A Nominal Size | Class A Operation Count (x 10^9) | Class A Mflop/s CRAY Y-MP/I | Class B Nominal Size | Class B Operation Count (x10^9) | Class B Mflop/s CRAY C90/I |
|---|---|---|---|---|---|---|---|
| Embarrassingly Parallel | EP | 2^28 | 26.68 | 211 | 2^30 | 100.9 | 543 |
| Multigrid | MG | 256^3 | 3.905 | 176 | 256^3 | 18.81 | 498 |
| Conjugate | CG | 14 x 10^3 | 1.508 | 127 | 75 x 10^3 | 54.89 | 447 |
| 3-D FFT PDE | FT | 256^2 x 128 | 5.631 | 196 | 512 x 256^2 | 71.37 | 560 |
| Integer Sort | IS | 2^23 x 2^19 | 0.7812 | 68 | 2^25 x 2^21 | 3.150 | 244 |
| LU Simulated CFD Application | LU | 64^3 | 64.57 | 194 | 102^3 | 319.6 | 493 |
| SP Simulated CFD Application | SP | 64^3 | 102.0 | 216 | 102^3 | 447.1 | 627 |
| BT Simulated CFD Application | BT | 64^3 | 181.3 | 229 | 102^3 | 721.5 | 572 |

## Linpack

- **Linpack（Linear system package）** 用高斯消元法求解一元N次稠密线性代数方程组的测试。用于测试高性能计算机浮点性能。
  - **Linpack**测试包括三类，**Linpack100、Linpack1000和HPL**。
  - **HPL即High Performance Linpack，也叫高度并行计算基准测试。** 用户在不修改任意测试程序的基础上，可以调节问题规模大小N（矩阵大小）、使用到的CPU数目和使用各种优化方法等来执行该测试程序，以获取最佳的性能。

## 其它常用测试程序

- 测试CPU+软件性能

- SPECjbb: 用于测试服务器端Java运行时环境（JRE）的性能，对JIT、GC（垃圾回收）、用户线程和OS施加了压力

- SPECjvm: 测试Java运行时环境（JRE）的性能，即JVM和Java核心函数库；包括编译、压缩、加解密、数据库、音频解码、FFT和LU等科学计算、sunflow和XML等22个测试程序，结果为每分钟多少个操作

- TPC事务处理测试: 测量系统处理事务能力，数据库访问和更新等，测试结果是每秒钟执行了多少个事务或交易（tps）：TPC-C模拟复杂查询环境，TPC-H建模即席查询和决策支持系统；TPC-E模拟证券经纪公司，B/S架构，事务类型增加到12种

- 浏览器性能测试: Octane等

- ……

## SPECjvm2008测试程序集

- startup.helloworld
- startup.compiler.compiler
- startup.compiler.sunflow
- startup.compress
- startup.crypto.aes
- startup.crypto.rsa
- startup.crypto.signverify
- startup.mpegaudio
- startup.scimark.fft
- startup.scimark.lu
- startup.scimark.monte_carlo
- startup.scimark.sor
- startup.scimark.sparse
- startup.serial
- startup.sunflow
- startup.xml.transform
- startup.xml.validation

- compiler.compiler
- compiler.sunflow
- compress
- crypto.aes
- crypto.rsa
- crypto.signverify
- derby
- mpegaudio
- scimark.fft.large
- scimark.lu.large
- scimark.sor.large
- scimark.sparse.large

- scimark.fft.small
- scimark.lu.small
- scimark.sor.small
- scimark.sparse.small
- scimark.monte_carlo
- serial
- sunflow
- xml.transform
- xml.validation
