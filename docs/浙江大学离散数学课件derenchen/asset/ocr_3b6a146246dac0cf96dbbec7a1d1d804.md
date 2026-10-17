# 有限数学归纳法：对于 $n_0 \le n \le n_k$ 的 $P(n)$

有限数学归纳法的前推公式表示：

$[P(n_0) \land \forall n(n_0 \le n \le n_{k-1} \land P(n)) \to P(n+1))] \to$  
$\forall n(n_0 \le n \le n_k \to P(n))$

+   1、归纳基础：$P(n_0)$  
+   2、归纳步骤：$\forall n(n_0 \le n \le n_{k-1} \land P(n)) \to P(n+1))$

# 有限数学归纳法：对于 $n_0 \le n \le n_k$ 的 $P(n)$

有限数学归纳法的后推公式表示：

$[P(n_k) \land \forall n(n_0+1 \le n \le n_k \land P(n)) \to P(n-1))] \to$  
$\forall n(n_0 \le n \le n_k \to P(n))$

+   1、归纳基础：$P(n_k)$  
+   2、归纳步骤：$\forall n(n_0+1 \le n \le n_k \land P(n)) \to P(n-1))$