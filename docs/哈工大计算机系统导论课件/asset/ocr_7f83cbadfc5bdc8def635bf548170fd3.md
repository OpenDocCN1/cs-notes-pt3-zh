# 虚拟内存作为内存管理的工具

+   - **Simplifying memory allocation 简化内存分配**
+     - 每个虚拟内存页面都要被映射到一个物理页面
+     - 一个虚拟内存页面可以被分配到不同的物理页面（可以不连续）

+   - **Sharing code and data among processes 简化代码和数据共享**
+     - 不同的虚拟内存页面被映射到相同的物理页面 (此例中的 PP 6)

![](bbox=[0.12, 0.48, 0.92, 0.92])