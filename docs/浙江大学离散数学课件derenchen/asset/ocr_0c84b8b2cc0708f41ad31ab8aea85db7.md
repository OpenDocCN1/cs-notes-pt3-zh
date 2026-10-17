# Relations关系

例（M=3）：
\[
R=\{(a,b)\mid a\equiv b\pmod{3},\ a,b\in I\}
\]
是整数集合 I 上模 3 同余的二元关系。
证明 R 是等价关系。

证明：由于 $3\mid(a-b)$ 等价于 $a\equiv b\pmod{3}$

+   1. $3\mid(a-a)$，自反性

+   2. 若 $3\mid(a-b)$，则 $3\mid(b-a)$，对称性

+   3. 若 $3\mid(a-b)$，$3\mid(b-c)$，则
+      $a-c=(a-b)+(b-c)$
+      $\Rightarrow 3\mid(a-c)$
+      满足传递性，故 $R$ 是等价关系