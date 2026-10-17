# 对增量 d<sub>i</sub> 的三种取法：

+   1) 线性探测再散列
+   
+   d<sub>i</sub> = c× i　最简单的情况　c=1

+   2) 二次探测再散列
+   
+   d<sub>i</sub> = 1<sup>2</sup>, -1<sup>2</sup>, 2<sup>2</sup>, -2<sup>2</sup>, ....

+   3) 随机探测再散列
+   
+   d<sub>i</sub> 是一组伪随机数列　或者
+   
+   d<sub>i</sub>=i× H<sub>2</sub>(key) (又称双散列函数探测)