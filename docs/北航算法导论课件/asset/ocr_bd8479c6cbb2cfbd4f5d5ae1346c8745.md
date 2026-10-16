# 3.1.2 O-notation: asymptotic upper bound (渐近上界)

**O – notation:** For a given function g(n), we denote by O(g(n)) the set of functions O(g(n)) = {f(n): there exist positive constants c and n₀ such that 0≤f(n)≤c g(n) for all n≥n₀}.

![](bbox=[0.12, 0.38, 0.34, 0.75])

![](bbox=[0.37, 0.38, 0.66, 0.75])

![](bbox=[0.7, 0.4, 0.95, 0.75])

+   - "f(n) = O(g(n))" indicates "f(n) ∈ O(g(n))"
+   - f(n) = Θ(g(n)) ⇒ f(n) = O(g(n))
+     ⇒ Θ(g(n)) ⊆ O(g(n))