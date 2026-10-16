# 可执行可链接格式 Executable and Linkable Format (ELF)

# 目标文件的标准二进制格式

+   - DOS操作系统（最简单）：COM格式，文件中仅包含代码和数据，且被加载到固定位置
+   - System V UNIX早期版本：COFF格式，文件中不仅包含代码和数据，还包含重定位信息、调试信息、符号表等其他信息，由一组严格定义的数据结构序列组成
+   - Windows：PE格式（COFF的变种），称为可移植可执行（Portable Executable，简称PE）
+   - Linux等类UNIX：ELF格式（COFF的变种），称为可执行可链接（Executable and Linkable Format，简称ELF）

# 一个统一的格式：

+   - 可重定位目标文件(.o),
+   - 可执行目标文件(a.out)
+   - 共享目标文件(.so)