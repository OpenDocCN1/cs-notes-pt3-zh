# 哈希（Hash）方法

查找及其分析：

查找方法同 hashing 函数的产生方法。

随机探测再散列、二次探测再散列和 hashing 法的成功、非成功查找的平均查找长度分析：

设 hashing 函数是均匀的，处理冲突后产生的地址也是均匀的。Hashing 表的长度为 m。

+   - 查找不成功的平均查找长度

$$U_n=\sum_{i=1}^{n+1} i\times q_i$$

其中：$q_i$ = 经过 i 次探测确定某结点不在 hashing 表中的概率。

= 第一直到第 i-1 次探测，由于冲突而失败的概率及第 i 次探测找到空单元的概率。

$$q_i=\frac{n}{m}\times\frac{n-1}{m-1}\times\frac{n-2}{m-2}\times\cdots\times\frac{n-i+2}{m-i+2}\left(1-\frac{n-(i-1)}{m-(i-1)}\right)$$

其中：$1\le i\le n+1$

可推出：$U_n=\sum_{i=1}^{n+1}i\times q_i=1/(1-n/(m+1))\approx\frac{1}{1-\alpha}$，其中 $\alpha=n/m$。