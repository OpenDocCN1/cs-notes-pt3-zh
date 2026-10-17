# 3.4 自下而上分析

# 3.4.2 句柄

句柄性质：

S⇒rm aABe⇒rm aAde⇒rm aAbcde⇒rm abbcde

+   1. 句柄的右边仅含终结符。

+   2. 如果文法二义，那么句柄可能不唯一。

例 E → E + E | E * E | (E) | id

E⇒rm E * E
⇒rm E * E + E
⇒rm E * E + id₃
⇒rm E * id₂ + id₃
⇒rm id₁ * id₂ + id₃

E⇒rm E + E
⇒rm E + id₃
⇒rm E * E + id₃
⇒rm E * id₂ + id₃
⇒rm id₁ * id₂ + id₃

在句型E * E + id₃中，句柄不唯一。