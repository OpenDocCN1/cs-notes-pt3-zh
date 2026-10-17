# # 规则1：约束变元的改名规则

+   - 例： 对公式\(\forall x(P(x, y) \rightarrow \exists yQ(x, y, z)) \wedge S(x, z)\) 进行换名，使各变元只呈一种形式出现。

# ## 解：

需要对约束变元\(x\)，\(y\)进行换名

\(\forall u(P(u, y) \rightarrow \exists vQ(u, v, z)) \wedge S(x, z)\)

# ### 不对的：

\(\forall u(P(u, \text{v}) \rightarrow \exists vQ(u, v, z)) \wedge S(x, z)\)

\(\forall u(P(u, y) \rightarrow \exists zQ(u, z, z)) \wedge S(x, z)\)