# 第1章的复习（1）

# 1. 算法复杂性的概念

+   - 时间、空间复杂性
+   - 5种渐进复杂性定义
+     - $O$、$o$、$\Omega$、$\omega$、$\Theta$ 的概念
+   - 证明
+     - $f(n)=?(g(n))$
+     - ?：5种渐进复杂性
+   - 注意：$O$、$\Omega$ 与 $o$、$\alpha$ 在定义上的区别：
+   - 存在正常数 $c$ 和 $n_0$，使得对所有 $n\ge n_0$ 有
+   - 对于任何正常数 $c>0$，存在正数 $n_0>0$

+   - $f(n)=O(g(n))\approx a\le b$；渐近上界
+   - $f(n)=\Omega(g(n))\approx a\ge b$；渐近下界
+   - $f(n)=\Theta(g(n))\approx a=b$；紧渐近界
+   - $f(n)=o(g(n))\approx a<b$；非紧上界
+   - $f(n)=\omega(g(n))\approx a>b$；非紧下界

# 2. 用特征方程解递归方程的通解