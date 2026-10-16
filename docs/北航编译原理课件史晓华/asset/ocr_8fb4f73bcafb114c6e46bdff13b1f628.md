# 12.1.2 存贮层次结构

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

![](bbox=[0.276, 0.278, 0.918, 0.344])