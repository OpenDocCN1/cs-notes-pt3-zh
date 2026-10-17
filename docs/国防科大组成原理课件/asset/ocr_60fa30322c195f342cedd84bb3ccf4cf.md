# PCI总线特性

+   - 支持多种类型的访问
+     - 内存读/写
+     - IO读/写
+     - 配置读/写
+   - 三态总线
+     - 使用中央仲裁器
+     - 支持总线停靠
+   - 支持软件自动配置
+   - 支持64位

| C/BE[3:0]# | Command Type |
|---|---|
| 0000 | Interrupt Acknowledge |
| 0001 | Special Cycle |
| 0010 | I/O Read |
| 0011 | I/O Write |
| 0100 | Reserved |
| 0101 | Reserved |
| 0110 | Memory Read |
| 0111 | Memory Write |
| 1000 | Reserved |
| 1001 | Reserved |
| 1010 | Configuration Read |
| 1011 | Configuration Write |
| 1100 | Memory Read Multiple |
| 1101 | Dual Address Cycle |
| 1110 | Memory Read Line |
| 1111 | Memory Write and Invalidate |