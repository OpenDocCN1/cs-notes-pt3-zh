(3) 若Xᵢ ∈ Vₙ 且 Xᵢ ::= y₁ y₂ ... yₖ，则按如下顺序计算FIRST(Xᵢ)
FIRST(Xᵢ) ← FIRST(y₁) - {ε}；
若 ε ∈ FIRST(y₁) 则将 FIRST(y₂) - {ε} 加入 FIRST(Xᵢ)；
若 ε ∈ FIRST(y₁)
    ε ∈ FIRST(y₂) 则将 FIRST(y₃) - {ε} 加入 FIRST(Xᵢ)
......
若 ε ∈ FIRST(yₖ₋₁) 则将 FIRST(yₖ) - {ε} 加入 FIRST(Xᵢ)
若 ε ∈ FIRST(y₁) ~ FIRST(yₖ)
    则将 ε 加入 FIRST(Xᵢ)

★ 注意：要顺序往下做，一旦不满足条件，过程就要中断进行
★ 得到 FIRST(Xᵢ)，即可求出 FIRST(α)。