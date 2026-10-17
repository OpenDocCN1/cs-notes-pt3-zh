# 例3：

$R=\{(a,b)\mid a\equiv b\pmod{3},\ a,b\in I\}$ 是整数集合 $I$ 上模 3 同余的二元关系。

证明 $R$ 是等价关系。

证明：由于 $3\mid(a-b)\ a\equiv b\pmod{3}$

+   1. $3\mid(a-a)$，自反性
+   2. 若 $3\mid(a-b)$，则 $3\mid(b-a)$ 对称性
+   3. 若 $3\mid(a-b)$，$3\mid(b-c)$，则
+      $$a-c=(a-b)+(b-c)$$
+      $$\Rightarrow 3\mid(a-c)$$

满足传递性，故 $R$ 是等价关系

商集：$I/R=\{[0],[1],[2]\}$

+   其中
+   - $[0]=\{\ldots,-6,-3,0,3,6,\ldots\}$
+   - $[1]=\{\ldots,-5,-2,1,4,7,\ldots\}$
+   - $[2]=\{\ldots,-4,-1,2,5,8,\ldots\}$