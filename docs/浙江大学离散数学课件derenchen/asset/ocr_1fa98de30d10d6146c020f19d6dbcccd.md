# 例9.5 设 $A、B$ 为集合，且 $Card\,A=\aleph_0$，$Card\,B=n$，$(n\ne0$ 是自然数$)$。求 $Card(A\times B)$。

**解法1：** 令 $A=\{a_0,a_1,\ldots\}$，$B=\{b_0,b_1,\ldots,b_{n-1}\}$。

对 $\langle a_i,b_j\rangle\in A\times B$ 和 $\langle a_k,b_l\rangle\in A\times B$，有

$\langle a_i,b_j\rangle=\langle a_k,b_l\rangle\Longleftrightarrow(a_i=a_k)\land(b_j=b_l)\Longleftrightarrow(i=k)\land(j=l)$。

定义 $f:A\times B\to\mathbb{N}$，$f(\langle a_i,b_j\rangle)=i\cdot n+j$，$(i=0,1,\ldots；j=0,1,\ldots,n-1)$。

则可以检验 $f$ 是 $A\times B$ 到 $\mathbb{N}$ 的双射函数，故

$$Card(A\times B)=Card\,\mathbb{N}=\aleph_0.$$

**解法2：** 因 $A$ 和 $B$ 都是可数集，由定理9.6，两个可数集的笛卡尔集

仍是可数集，故

$$Card(A\times B)=\aleph_0.$$