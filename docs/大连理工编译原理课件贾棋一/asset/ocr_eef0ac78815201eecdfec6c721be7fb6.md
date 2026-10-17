# ## 3.2 语言和文法

# ### 例 算术表达文法

E→E+T|T
T→T*F|F
F→(E)|id

(T+T...+T)
(F*F...*F)

# ### 消除左递归后文法

E→TE′
E′→+TE′|ε
T→FT′
T′→*FT′|ε
F→(E)|id