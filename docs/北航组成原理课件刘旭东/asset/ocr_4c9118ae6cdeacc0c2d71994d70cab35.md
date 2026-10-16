# 4.4 磁盘的性能参数

# 磁盘的类型

+   - **Floppy Disk**
+     - 尺寸：5.25 inch, 3.5 inch
+     - 容量：360KB, 1.2MB, 720KB, 1.44MB

+   - **IDE（Integrated Drive Electronics）Hard Disk**
+     - 80年代出现，主要为基于IBM PC兼容机所用，属于低价位磁盘，由系统BIOS(Basic Input Output System)处理磁盘的读写等操作。
+     - 早期可能是BIOS程序员的失误，IDE磁盘的地址被定义为：Head #(4位，从0开始)，Cylinder#(10位，从0开始)，Sector#(6位，从1开始)，所以磁盘最大容量限制：16*63*1024*512Bytes（528MB）。
+     - 后来，出现了EIDE（Extendex IDE）Hard Disk，支持LBA(Large Block Address)地址模式，扇区地址可以从0到2²⁴-1。