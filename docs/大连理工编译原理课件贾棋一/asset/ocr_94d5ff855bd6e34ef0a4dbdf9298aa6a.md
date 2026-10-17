# # 3.1 上下文无关文法

最左推导与最右推导

E → E+E|E*E|(E)|-E|id

E ⇒ -E ⇒ -(E) ⇒ -(E+E)

最左推导

E ⇒ lm-E ⇒ lm-(E) ⇒ lm-(E+E)
⇒ lm-(id+E) ⇒lm -(id+id)

最右推导（规范推导）

E ⇒ rm-E ⇒ rm-(E) ⇒ rm-(E+E)
⇒ rm-(E+id) ⇒rm -(id+id)