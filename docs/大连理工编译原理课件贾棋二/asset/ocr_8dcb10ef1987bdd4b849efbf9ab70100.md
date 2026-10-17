# # 语法分析内容总结

例1 解答：
提取左因子，
将P->bPc | bQc变为
P ->bP'
P'-> Pc | Qc
消除左递归， 将 Q->Qa | a 变为
Q->aQ'
Q'->aQ' | ε

G[S]:
S->aSb | P
P->bPc |bQc
Q->Qa | a