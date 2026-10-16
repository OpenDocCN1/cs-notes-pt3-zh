# 4.4.2 Using the master method: some examples

T(n) = aT(n/b) + f(n),

T(n) = { Θ(n^{log_b a}), f(n) = O(n^{log_b a - ε}) ; Θ(n^{log_b a} lg n), f(n) = Θ(n^{log_b a}) ; Θ(f(n)), f(n) = Ω(n^{log_b a + ε}) and a f(n/b) ≤ c f(n) for large n } ∃ε > 0 , c < 1

+   - **T(n)=9T(n/3)+n**
+     a = 9, b = 3, f(n) = n ⇒ n^{log_b a} = n^{log_3 9} = n^2 = Θ(n^2)
+     ⇒ f(n) = O(n^{log_3 9 - ε}), where ε = 1 ⇒ T(n) = Θ(n^2)

+   - **T(n)=T(2n/3)+1**
+     a = 1, b = 3/2, f(n) = 1 ⇒ n^{log_b a} = n^{log_{3/2} 1} = n^0 = 1
+     ⇒ f(n) = Θ(n^{log_3 a}) = Θ(1) ⇒ T(n) = Θ(lg n)