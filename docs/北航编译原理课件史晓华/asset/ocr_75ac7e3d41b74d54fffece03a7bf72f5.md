# 2.构造集合FOLLOW的算法

设S, A, B∈Vₙ，

算法：连续使用以下规则，直至FOLLOW集合不再扩大

+   (1) 若S为识别符号,则把“#”加入FOLLOW(S)中

+   (2) 若A::=αBβ (β≠ε),则把FIRST(β)-{ε}加入FOLLOW(B)

+   (3) 若A::=αB 或A::=αBβ，且β⇒ε则把FOLLOW(A)加入FOLLOW(B)

注：FOLLOW集合中不能有ε