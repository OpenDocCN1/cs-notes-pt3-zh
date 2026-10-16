# 4.4.2 Using the master method: some examples

T(n) = a T(n / b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{(log_b a) - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{(log_b a)+ε}) and a f(n / b) ≤ c f(n) for large n } , ∃ ε > 0 , c < 1

+   - T(n) = 3 T(n/4) + n lg n

a = 3, b = 4, f(n) = n lg n ⇒ n^{log_b a} = n^{log_4 3} = O(n^{0.793})

⇒ f(n) = Ω(n^{(log_4 3)+ε}), where ε ≈ 0.2, and for sufficiently large n, a f(n / b) = 3 (n / 4) lg(n / 4) ≤ (3 / 4) n lg n = c f(n) for c = 3 / 4

⇒ T(n) = Θ(n lg n)