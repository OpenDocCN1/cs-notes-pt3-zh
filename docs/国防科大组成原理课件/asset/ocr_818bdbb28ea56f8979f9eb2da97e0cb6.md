# OpenMP的制导-数据域属性子句

数据域属性子句用来定义变量范围，一般与parallel、for和sections语句配合使用

+   - private子句：表示它列出的变量对于每个线程是局部的
+   - shared子句：表示它列出的变量被线程队列中的所有线程共享
+   - default子句：表示并行域的所有变量的默认属性（如可以是private、shared、none）
+   - firstprivate子句：含private子句的操作，初始化为并行域外同名变量值
+   - lastprivate子句：含private子句的操作，并将值复制给并行域外同名变量
+   - threadprivate编译制导语句：将全局变量变成每个线程私有
+   - copyin子句：赋予线程中变量与主线程中threadprivate同名变量的值
+   - reduction子句：用来归约其列表中出现的变量。