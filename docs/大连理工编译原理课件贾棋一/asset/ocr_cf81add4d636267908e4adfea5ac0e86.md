# 3.1 上下文无关文法

上下文无关文法是四元组（\(V_T, V_N, S, P\)）

\(V_T\)：终结符集合(非空有限集合，记号名是其同意词)

\(V_N\)：非终结符集合（非空有限集合，\(V_T \cap V_N = \phi\)）

S：开始符号(非终结符)

P：产生式集合，产生式形式：\(A \rightarrow \alpha\)，\(A \in V_N, \alpha \in (V_T \cup V_N)^*\)

例（{id, +, *, -, (, )}, {expr, op}, expr, P）

expr → expr op expr
expr → - expr
op → +

expr → (expr)
expr → id
op → *