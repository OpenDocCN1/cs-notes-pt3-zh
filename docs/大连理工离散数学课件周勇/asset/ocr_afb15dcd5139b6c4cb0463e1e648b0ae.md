# # 四、关系的闭包运算

定理：设\(X\)是集合，\(R\)是\(X\)中的二元关系，于是有

+   (1) 如果\(R\)是自反的，那么\(s(R),t(R)\)也是自反的；

+   (2) 如果\(R\)是对称的，那么\(r(R),t(R)\)也是对称的；

+   (3) 如果\(R\)是可传递的，那么\(r(R)\)也是可传递的。

证明（1）：若\(R\)是自反的，则对于所有的\(x \in X\)都有

\(\langle x, x \rangle \in R \Rightarrow \langle x, x \rangle \in R \cup R^{-1} = s(R)\)

\(\langle x, x \rangle \in R \Rightarrow \langle x, x \rangle \in \bigcup_{i=1}^\infty R^i = t(R)\)

即\(s(R),t(R)\)是自反的