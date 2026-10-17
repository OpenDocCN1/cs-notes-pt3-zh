# 例（续）

例：前面例子中，无∃前缀范式为

(∀y)(∀z)(∀v)(A(a, c, f(y), v) ∧ ¬B(g(y, z), b, h(y, z, v)) ∧ ¬H(z))

H₀ = {a, b, c}

H₁ = H₀ ∪ {f(a), f(b), f(c), g(a, a), g(a, b), g(b, a), g(b, b), g(c, a), g(c, b), g(a, c), g(b, c), g(c, c), h(a, a, a), h(a, a, b), h(a, a, c), h(a, b, a), h(a, b, b), h(a, b, c), h(a, c, a), h(a, c, b), h(a, c, c), h(b, a, a), h(b, a, b), h(b, a, c), h(b, b, a), h(b, b, b), h(b, b, c), h(b, c, a), h(b, c, b), h(b, c, c), h(c, a, a), h(c, a, b), h(c, a, c), h(c, b, a), h(c, b, b), h(c, b, c), h(c, c, a), h(c, c, b), h(c, c, c)}

H₂ = H₁ ∪ {f(x)|x∈ H₁} ∪ {g(x, y)|x, y∈ H₁} ∪ {h(x, y, z)|x, y,z ∈ H₁}

……