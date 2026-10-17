# Coremark - 试图替换Dhrystone

+   - 优点：更为真实的应用，编译不能预计算，库的影响较小
+     - 矩阵操作，代表常见的数学操作
+     - 链表操作，覆盖常见的指针的使用
+     - 状态机操作，覆盖数据相关的分支
+     - CRC操作，嵌入式常见操作

CoreMark consists of the following C source

+   - coremark.h
+   - core_main.c
+   - core_list_join.c
+   - core_matrix.c
+   - core_state.c
+   - core_util.c
+   - simple/core_portme.c
+   - simple/core_portme.h

Cortex-M4 processor running at 168MHz.
2K performance run parameters for coremark.
CoreMark Size : 666
Total ticks : 3512687483
Total time (secs): 20.908854
Iterations/Sec : 478.266287
Iterations : 10000
Compiler version : ARM C/C++ Compiler, 5.03 [Build 24]
Compiler flags : -O3 -Otime --loop_optimization_level=2
Memory location : STACK
seedcrc : 0xe9f5
[0]crcclist : 0xe714
[0]crcmatrix : 0x1fd7
[0]crcstate : 0x8e3a
[0]crcfinal : 0x988c
Correct operation validated. See readme.txt for run and results.
CoreMark 1.0 : 478.266287 / ARM C/C++ Compiler, 5.03 [Build 24]
--loop_optimization_level=2 / STACK