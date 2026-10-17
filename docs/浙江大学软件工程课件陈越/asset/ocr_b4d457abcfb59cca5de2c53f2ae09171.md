# § 1. 基本概念

+   - **白盒测试**(white-box，or open-box, clear-box testing):
+     Use the structure of the program to test.　　　—— Structural testing

**主要问题：** 穷尽测试(complete test)通常是不可能的。

例：(Black-box) 程序要求输入3个整形数据。若字长16位，则各种可能输入的排列组合共有

\[
2^{16}\times 2^{16}\times 2^{16}\approx 3\times 10^{14}\text{（种）}
\]

若程序执行需10^-3秒，则对于所有合法输入的测试大约需用一万年，而且还应测试输入非法数据的情况。