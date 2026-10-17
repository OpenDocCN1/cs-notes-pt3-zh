# 主流多核处理器Cache结构

+   - 主流商用多核处理器一般采用共享最后一级Cache结构
+     - 一级及二级Cache私有，三级Cache（最后一级Cache）共享
+     - 有些处理器有片外L4 Cache

表：商用多核处理器主要参数示例

|  | IBM Power8 | Intel Haswell | Oracle SPARC T5 | 龙芯3A3000 |
|---|---|---|---|---|
| Cores per chip | 12 | 4 | 16 | 4 |
| Threads per core | 8 | 2 | 8 | 1 |
| L1 ICache per core | 32KB | 32KB | 16KB | 64KB |
| L1 DCache per core | 64KB | 32KB | 16KB | 64KB |
| L2 Cache per core | 512KB | 256KB | 128KB | 256KB |
| On-chip shared LLC | 96MB | 8MB | 8MB | 8MB |