# # 4.4 L属性的自下而上计算

# ## 属性的位置不能预测

S → aAC
S → bABC
C → c

C.i := A.s
C.i := A.s
C.s := g(C.i)

# ### 增加标记非终结符

S → aAC
S → bABMC
C → c
M → ε

C.i := A.s
M.i := A.s; C.i := M.s
C.s := g(C.i)
M.s := M.i

| S→aAC   |    |
|---|---|
| S→bABMC |    |
| C→c     | val [top]=g(val [top-1]) |
| M→ ε    | val [top+1]=val [top-1] |