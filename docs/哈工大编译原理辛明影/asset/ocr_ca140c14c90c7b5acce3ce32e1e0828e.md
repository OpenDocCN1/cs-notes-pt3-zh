# 7.6.1 布尔表达式的回填式翻译

B → B₁ or M B₂
{backpatch(B₁.falselist, M.quad);
B.truelist:=merge(B₁.truelist, B₂.truelist);
B.falselist := B₂.falselist}

![](bbox=[0.43, 0.43, 0.95, 0.85])

M → ε
{M.quad:=nextquad
M.truelist:=B.truelist);
M.falselist := B.falselist}