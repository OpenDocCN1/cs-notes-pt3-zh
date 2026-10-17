# 例

求(∃x)(∀y)(∀z)(∃u)(∀v)(∃w)(A(a, x, f(y), v) ∧ ¬B(u, b, w) ∧ ¬H(z)) 的无∃前束范式。

解：(∃x)(∀y)(∀z)(∃u)(∀v)(∃w)(A(a, x, f(y), v) ∧ ¬B(u, b, w) ∧ ¬H(z))

↓（消去∃x）

(∀y)(∀z)(∃u)(∀v)(∃w)(A(a, c, f(y), v) ∧ ¬B(u, b, w) ∧ ¬H(z))

↓（消去∃u）

(∀y)(∀z)(∀v)(∃w)(A(a, c, f(y), v) ∧ ¬B(g(y, z), b, w) ∧ ¬H(z))

↓（消去∃w）

(∀y)(∀z)(∀v)(A(a, c, f(y), v) ∧ ¬B(g(y, z), b, h(y, z, v)) ∧ ¬H(z))