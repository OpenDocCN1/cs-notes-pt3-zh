# ELF目标文件

+   - **.symtab 节**
+     ✓ 存放函数和全局变量（符号表）信息，它不包括局部变量
+   - **.rel.text 节**
+     ✓ .text节的重定位信息，用于重新修改代码段的指令中的地址信息
+   - **.rel.data 节**
+     ✓ .data节的重定位信息，用于对被模块使用或定义的全局变量进行重定位的信息
+   - **.debug 节**
+     ✓ 调试用符号表 (gcc -g)
+   - **strtab 节**
+     ✓ 包含symtab和debug节中符号及节名
+   - **Section header table (节头表)**
+     ✓ 每个节的节名、偏移和大小

+   - **ELF 头**
+   - **.text 节**
+   - **.rodata 节**
+   - **.data 节**
+   - **.bss 节**
+   - **.symtab 节**
+   - **.rel.txt 节**
+   - **.rel.data 节**
+   - **.debug 节**
+   - **.strtab 节**
+   - **.line 节**
+   - **Section header table (节头表)**