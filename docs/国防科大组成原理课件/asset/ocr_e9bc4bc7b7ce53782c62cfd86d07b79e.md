# 访存对象

+   - 存储器按字节编址
+     - 所有地址都是字节地址
+     - 访问长度：字节、半字、字、双字
+   - 访存地址是否对齐（Aligned vs. Misaligned）
+     - 地址对齐简化硬件设计：如字地址最低两位为0
+     - 跨数据通路边界的访问可能需要访问两次RAM
+     - 如何支持不对齐访问（如串操作）
+   - 大尾端（Big Endian）和小尾端（Little Endian）
+     - Little Endian地址指向一个字的最右字节
+     - Big Endian 反之