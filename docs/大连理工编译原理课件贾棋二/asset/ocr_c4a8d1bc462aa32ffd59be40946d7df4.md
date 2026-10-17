# # L属性的自下而上计算

# ## 特殊情况二： 分析栈上的继承属性

+   - 属性位置能预测

例 int p, q, r

D → T {L.in := T.type} L

T→ int {T. type := integer}

T→ real {T. type := real}

L→ {L1.in := L.in }

L1, id {addtype (id.entry, L.in )}

L→ id {addtype (id.entry, L.in )}