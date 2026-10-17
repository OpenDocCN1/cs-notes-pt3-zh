# § 6.2 集合的运算

# 一、集合的基本运算

设 A,B 是集合。

+   1. A 与 B 的并：$A∪B=\{x\mid x∈A∨x∈B\}$。
+   2. A 与 B 的交：$A∩B=\{x\mid x∈A∧x∈B\}$。
+   3. A 与 B 的差（B 对 A 的相对补）：$A−B=\{x\mid x∈A∧x∉B\}$。
+   4. A 与 B 的对称差：$A⊕B=(A−B)∪(B−A)=(A∪B)−(A∩B)$。
+   5. A 的补集（或称绝对补）：$\sim A=E−A=\{x\mid x∈E∧x∉A\}$。

注：（1）“并”和“交”运算可以推广到各个集合：

$\displaystyle \bigcup_{i=1}^{n}A_i=A_1∪A_2∪\cdots∪A_n=\{x\mid x∈A_1∨x∈A_2∨\cdots∨x∈A_n\}$

$\displaystyle \bigcap_{i=1}^{n}A_i=A_1∩A_2∩\cdots∩A_n=\{x\mid x∈A_1∧x∈A_2∧\cdots∧x∈A_n\}$