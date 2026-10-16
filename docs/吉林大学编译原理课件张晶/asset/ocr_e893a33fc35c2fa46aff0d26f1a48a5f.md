# 假设有数组类型的变量声明如下：

A :array [L1..U1] [L2 .. U2]⋯[Ln .. Un] of T ; (n ≥ 1)

# 数组类型的内部表示 其中Di=Ui−Li+1

| Size | Kind | Low | Up | ElemType |
|------|------|-----|----|----------|
| D₁ × D₂ × ⋯ × Dₙ × Size(T) | ArrayTy | L₁ | U₁ |  |
| D₂ × D₃ × ⋯ × Dₙ × Size(T) | ArrayTy | L₂ | U₂ |  |
| ⋯ | ⋯ | ⋯ | ⋯ | ⋯ |
| Dₖ × Dₖ₊₁ × ⋯ × Dₙ × Size(T) | ArrayTy | Lₖ | Uₖ |  |
| ⋯ | ⋯ | ⋯ | ⋯ | ⋯ |
| Dₙ₋₁ × Dₙ × Size(T) | ArrayTy | Lₙ₋₁ | Uₙ₋₁ |  |
| Dₙ × Size(T) | ArrayTy | Lₙ | Uₙ |  |
| Size(T) | Ptr(T) | …… |  |  |