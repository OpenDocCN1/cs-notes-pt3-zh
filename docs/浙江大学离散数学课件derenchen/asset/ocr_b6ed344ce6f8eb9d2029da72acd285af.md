# 证明集合恒等式的方法：欲证 $P=Q$

+   1. 利用命题演算方法证明 $P\subseteq Q$ 且 $Q\subseteq P$。即证
+      $$\forall x\in P\Rightarrow x\in Q\quad\text{且}\quad\forall x\in Q\Rightarrow x\in P$$

+   2. 直接利用运算律和已知的集合恒等式做恒等变形。

# 例 6.1 证明 $A-(B\cup C)=(A-B)\cap(A-C)$

证：对任意的 $x$

$$x\in A-(B\cup C)\Leftrightarrow x\in A\land x\notin(B\cup C)$$

$$\Leftrightarrow x\in A\land x\notin B\land x\notin C$$

$$\Leftrightarrow (x\in A\land x\notin B)\land(x\in A\land x\notin C)$$

$$\Leftrightarrow x\in(A-B)\land x\in(A-C)$$

$$\Leftrightarrow x\in(A-B)\cap(A-C)$$

$$\therefore A-(B\cup C)=(A-B)\cap(A-C)$$