# 打桩回顾

+   - **编译时**
+     - 对malloc/free的显式调用将宏扩展到对mymalloc/myfree的调用
+   - **链接时**
+     - 使用链接技巧trick来获得特殊的符号名解析
+       - malloc → __wrap_malloc
+       - __real_malloc → malloc
+   - **加载/运行时**
+     - 实现malloc/free的自定义版本：用不同的名字，使用动态链接来加载库malloc/free