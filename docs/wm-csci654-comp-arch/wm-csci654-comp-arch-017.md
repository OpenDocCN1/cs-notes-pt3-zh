# 017：缓存设计 1 💾

![](img/92d85e15a1465e52e0e23e65c4ef91cd_1.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_2.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_3.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_4.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_5.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_6.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_7.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_9.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_11.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_13.png)

在本节课中，我们将要学习计算机体系结构中的一个核心组件：缓存。我们将从内存系统的基本概念出发，探讨为什么需要缓存，并详细介绍缓存的工作原理、设计权衡以及关键概念，如局部性、缓存行和关联度。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_15.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_17.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_18.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_19.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_20.png)

## 内存系统与冯·诺依曼瓶颈

![](img/92d85e15a1465e52e0e23e65c4ef91cd_21.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_22.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_24.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_26.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_27.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_28.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_30.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_31.png)

上一节我们介绍了处理器与内存系统的基本结构。在冯·诺依曼架构中，指令和数据都存储在内存中。处理器需要从内存中读取数据以进行计算，并将结果写回内存。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_33.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_35.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_37.png)

冯·诺依曼在设计时就预见到，内存系统的发展速度可能跟不上处理器核心的发展。处理器核心可以运行得非常快，但将数据从内存带到核心以及将数据存回内存会花费大量时间，这将成为性能瓶颈，即**冯·诺依曼瓶颈**。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_38.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_39.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_40.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_42.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_44.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_45.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_46.png)

## 内存技术：SRAM 与 DRAM

![](img/92d85e15a1465e52e0e23e65c4ef91cd_47.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_48.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_50.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_51.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_52.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_53.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_54.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_55.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_56.png)

为了理解缓存的作用，我们首先需要了解两种主要的内存技术：SRAM 和 DRAM。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_58.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_59.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_60.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_62.png)

以下是 SRAM 与 DRAM 的关键特性对比：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_64.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_65.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_66.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_67.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_68.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_70.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_72.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_73.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_74.png)

*   **基本单元**：SRAM 通常由 6 个晶体管构成一个存储单元。DRAM 的基本单元是一个电容加一个晶体管（电容由晶体管本身构成），因此每个比特只需要 1 个晶体管。
*   **数据保持**：SRAM 在通电期间可以一直保持数据。DRAM 需要定期刷新。
*   **速度**：SRAM 非常快，访问延迟可以低至 1 个周期或最多几十个周期。DRAM 较慢，延迟通常在几十到几百个周期。
*   **密度与成本**：SRAM 的密度低，占用更多晶体管和面积，因此无法构建非常大的存储，且每比特成本更高。DRAM 可以构建更大的存储，每比特成本更低。
*   **功耗**：SRAM 功耗较高。DRAM 功耗较低。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_76.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_77.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_78.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_79.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_81.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_83.png)

没有一种技术适用于所有场景，总是存在权衡，我们需要在合适的位置选择最合适的技术。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_85.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_86.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_87.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_88.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_89.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_90.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_92.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_94.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_95.png)

## 缓存的引入与作用

![](img/92d85e15a1465e52e0e23e65c4ef91cd_96.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_97.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_99.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_101.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_102.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_104.png)

随着处理器时钟频率达到数 GHz，需要大量数据来维持核心忙碌，此时 DRAM 的速度已无法满足需求，而 SRAM 又无法提供足够大的容量（通常只有几 KB 到几 MB）。因此，我们在核心和内存之间引入了**缓存**。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_105.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_106.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_107.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_108.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_109.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_111.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_112.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_113.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_114.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_116.png)

这就像在家（缓存）存放最常用的物品，而在租用的大型仓库（主存）存放不常用的物品。缓存存储频繁使用的数据，以提高访问速度。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_118.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_119.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_120.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_122.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_123.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_125.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_126.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_128.png)

缓存对程序员是透明的，即程序无需为缓存系统修改地址访问方式。它只是一种性能优化方法。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_130.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_132.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_133.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_135.png)

缓存的主要作用包括：
*   存储频繁使用的数据。
*   提高进入核心的有效带宽（如果缓存命中率高）。
*   将平均访问延迟从数百个周期降低到几个周期。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_137.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_138.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_139.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_140.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_141.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_142.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_144.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_145.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_146.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_148.png)

## 多级缓存层次结构

![](img/92d85e15a1465e52e0e23e65c4ef91cd_150.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_152.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_154.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_156.png)

即使缓存由 SRAM 构建，其设计方式也不同，可以提供不同的带宽和延迟。因此，我们通常构建多级缓存。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_158.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_159.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_161.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_162.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_164.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_166.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_167.png)

以下是多级缓存层次结构的特点：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_169.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_170.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_172.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_174.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_175.png)

*   **越靠近核心**：缓存容量越小，速度越快（延迟越低），带宽越高（在芯片内部）。
*   **越靠近内存（DRAM）**：缓存容量越大，但延迟也越长。
*   **最后一级缓存**：最靠近 DRAM 的缓存（如 L3）通常称为最后一级缓存。它充当 DRAM 的代理，所有读写请求都需要经过它。从 DRAM 的角度看，它也是一个带宽加速器，如果命中率高，可以有效提升从最后一级缓存输出的带宽。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_177.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_179.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_180.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_182.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_183.png)

增加缓存层级会引入额外的查找和传输延迟，但也能通过提高命中率来降低潜在的平均延迟。缓存层级数量没有固定答案，取决于具体设计权衡。例如，AMD GPU 架构在几年内就从两级缓存过渡到了四级缓存。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_185.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_187.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_189.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_191.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_192.png)

## 局部性原理

![](img/92d85e15a1465e52e0e23e65c4ef91cd_194.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_196.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_198.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_199.png)

在深入缓存实现之前，我们需要理解**局部性**这个概念，它描述了程序访问内存的模式。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_201.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_202.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_203.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_205.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_206.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_208.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_209.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_211.png)

局部性主要分为两类：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_213.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_214.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_215.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_217.png)

*   **时间局部性**：如果程序访问了一个数据项，那么它很可能在不久的将来再次访问相同的数据项。例如，循环中反复访问同一个变量。
*   **空间局部性**：如果程序访问了一个内存位置，那么它很可能在不久的将来访问附近的内存位置。例如，按顺序遍历数组。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_219.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_221.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_222.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_223.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_225.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_226.png)

大多数程序都遵循这些模式。缓存的设计正是为了利用这些模式：
*   针对时间局部性，缓存会保留最近访问过的数据。
*   针对空间局部性，当访问一个数据时，缓存会将其附近的一组数据（一个缓存行）一起取来保存。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_228.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_229.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_231.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_233.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_235.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_237.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_238.png)

## 缓存的基本操作与缓存行

![](img/92d85e15a1465e52e0e23e65c4ef91cd_239.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_241.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_243.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_244.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_245.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_246.png)

现在，我们将缓存视为一个黑盒，看看其基本接口和行为。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_247.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_249.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_250.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_252.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_254.png)

当核心发起一个读请求，例如访问地址 A，缓存需要检查数据是否已在其中。缓存存储数据的基本单位称为**缓存行**。例如，数据总线宽度为 64 字节，那么即使核心只请求 4 字节数据，缓存也会传输整个 64 字节的缓存行。缓存行的大小（如 32、64、128 字节）是对齐的。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_256.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_258.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_260.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_262.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_263.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_265.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_267.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_268.png)

缓存需要知道里面存储了哪些地址的数据。为此，每个缓存行除了存储数据本身，还存储一个**标签**，用于记录该行数据对应的内存地址。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_270.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_272.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_273.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_274.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_276.png)

一次缓存访问可能有两种结果：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_277.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_279.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_281.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_282.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_284.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_286.png)

1.  **缓存命中**：请求的数据在缓存中。缓存直接将该数据返回给核心，速度非常快。
2.  **缓存未命中**：请求的数据不在缓存中。缓存需要向下一级存储（可能是更低级缓存或主存）发起读请求，等待数据返回。数据返回后，缓存会将其存入一个空闲位置，并设置好标签，然后将数据送给核心。如果缓存已满，则需要选择一个**牺牲块**将其替换出去。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_288.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_290.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_291.png)

## 缓存行大小的权衡

![](img/92d85e15a1465e52e0e23e65c4ef91cd_293.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_295.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_297.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_298.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_300.png)

缓存行大小是一个重要的设计参数。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_302.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_304.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_306.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_308.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_310.png)

以下是不同缓存行大小的优缺点：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_312.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_314.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_316.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_317.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_319.png)

*   **大缓存行的优点**：
    *   更好地利用空间局部性。
    *   标签存储开销相对更小（因为标签数量不变，但每行数据更多）。
*   **大缓存行的缺点**：
    *   缓存中可存放的行数更少。
    *   带宽利用率可能降低（如果传输的数据中只有一小部分被用到）。
    *   可能增加延迟和能耗。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_321.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_322.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_324.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_326.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_328.png)

选择取决于程序的空间局部性强弱。数据总线宽度、缓存行大小、上下级接口宽度可以是相互独立的参数。例如，**扇区缓存**使用较大的缓存行但较小的数据总线，可以兼顾低开销和较好的带宽利用率。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_330.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_332.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_334.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_336.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_338.png)

## 缓存的组织方式：关联度

![](img/92d85e15a1465e52e0e23e65c4ef91cd_340.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_342.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_343.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_345.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_347.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_349.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_351.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_352.png)

缓存内部如何根据地址找到数据？一种直观的设计是为每个缓存行配备一个比较器，将输入地址与所有标签同时比较。这称为**全关联**缓存。其优点是灵活，任何数据可以存放在任何位置，命中率高。缺点是硬件成本（比较器数量、电路复杂度）高。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_354.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_356.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_358.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_359.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_360.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_362.png)

为了降低硬件成本，引入了**直接映射**缓存。它将缓存划分为若干组，通过地址中的几位（索引位）直接确定一个数据块只能存放在哪个唯一的组里。这样只需要一个比较器。缺点是容易发生冲突，即多个频繁访问但索引相同的数据会互相踢出，即使缓存其他部分空闲。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_364.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_366.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_368.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_370.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_371.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_373.png)

折中的方案是**组相联**缓存。缓存被分为 S 个组，每个组有 W 个路。一个数据块可以存放在对应组内的任意一个路中。这需要 W 个比较器。W 被称为**相联度**。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_375.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_377.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_379.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_381.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_383.png)

这是一个从直接映射到全关联的谱系：
*   **直接映射**： 相联度 = 1。成本最低，冲突概率最高。
*   **组相联**： 1 < 相联度 < 缓存总行数。在成本和性能间权衡。
*   **全关联**： 相联度 = 缓存总行数。性能最好，成本最高。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_385.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_387.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_389.png)

选择哪种方式取决于性能需求与硬件预算。缓存未命中惩罚越高，越倾向于使用高相联度。现代 L1 缓存常用 4 路或 8 路组相联，最后一级缓存可能用到 16 路或 32 路。全关联缓存由于成本过高很少使用，但 TLB 等对未命中惩罚极高的特殊缓存可能会采用。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_391.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_392.png)

## 替换策略

![](img/92d85e15a1465e52e0e23e65c4ef91cd_394.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_395.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_397.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_399.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_401.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_403.png)

当缓存已满且发生未命中时，需要从候选位置中选择一个牺牲块替换出去。常用的替换策略包括：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_405.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_406.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_408.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_409.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_410.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_412.png)

以下是几种常见的缓存替换策略：

![](img/92d85e15a1465e52e0e23e65c4ef91cd_414.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_415.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_416.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_418.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_419.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_421.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_422.png)

*   **最近最少使用**： 替换最长时间未被访问的块。理论上能提供较好的命中率，但实现成本较高，尤其是对于大缓存和多路组相联缓存。
*   **先进先出**： 替换最早进入缓存的块。实现简单，性能尚可。
*   **随机替换**： 随机选择一个块替换。实现非常简单，在某些访问模式下（如“计算一次”的数据），其性能可能优于 LRU。
*   **最近最多使用**： 替换最近被访问过的块。这听起来反直觉，但在某些特定场景下（如缓存颠簸），它可能表现更好，因为它倾向于保护那些较早被访问但后续还会用到的数据（如卷积核）。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_423.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_424.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_426.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_427.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_428.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_429.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_431.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_433.png)

## 总结

![](img/92d85e15a1465e52e0e23e65c4ef91cd_435.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_437.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_439.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_441.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_443.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_445.png)

本节课我们一起学习了缓存设计的基础知识。我们从冯·诺依曼瓶颈和内存技术差异出发，理解了引入缓存的必要性。缓存通过利用程序的时间局部性和空间局部性，存储频繁访问的数据，从而降低平均访问延迟，提升有效带宽。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_447.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_449.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_451.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_453.png)

我们探讨了多级缓存层次结构、缓存行的概念以及大小权衡。重点分析了缓存的组织方式，包括直接映射、组相联和全关联缓存，以及它们如何在硬件成本与性能之间取得平衡。最后，我们介绍了当缓存满时决定替换哪个数据块的几种策略。

![](img/92d85e15a1465e52e0e23e65c4ef91cd_455.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_456.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_458.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_460.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_461.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_462.png)

![](img/92d85e15a1465e52e0e23e65c4ef91cd_464.png)

下一节课，我们将继续探讨缓存设计的另一个重要方面：写操作的处理策略。