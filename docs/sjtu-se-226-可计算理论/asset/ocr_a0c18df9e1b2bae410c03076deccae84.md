# Effectiveness of Recursion

Consider f defined by the following recursion

f(e1, e2, x̃, 0) ≃ φ_{e1}^{(n)}(x̃) ≃ ψ_{U}^{(n)}(e1, x̃)

and

f(e1, e2, x̃, y + 1) ≃ φ_{e2}^{(n+2)}(x̃, y, f(e1, e2, x̃, y)) ≃ ψ_{U}^{(n+2)}(e2, x̃, y, f(e1, e2, x̃, y))

By S-m-n Theorem, there is a total computable function r(e1, e2) such that

φ_{r(e1,e2)}^{(n+1)}(x̃, y) ≃ f(e1, e2, x̃, y)