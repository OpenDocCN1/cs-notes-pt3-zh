# 6.5.2 Halstead方法（Halstead’s Metrics）

M. H. Halstead, et al., Elements of Software Science, Elsevier North Holland, pp. 54-67, 1977

根据程序中运算符和操作符（变量和常数）的总数度量程序的复杂度

N₁为程序中运算符出现的总次数，N₂为操作符出现的总次数，程序长度N定义为：N=N₁+N₂

运算符包括：

+   - 算术运算符
+   - 赋值符（=或:=）
+   - 逻辑运算符
+   - 分界符（，或；或：）
+   - 关系运算符
+   - 括号运算符
+   - 子程序调用符
+   - 数组操作符
+   - 循环操作符等

特别地，成对的运算符，例如“begin…end”、“for…to”、“repeat …until”、“while…do”、“if…then…else”、“（…）”等都当做单一运算符