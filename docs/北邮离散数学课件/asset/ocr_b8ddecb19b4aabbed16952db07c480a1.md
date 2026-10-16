![](bbox=[0.02, 0.09, 0.18, 0.68])

+   - Basis step: Clearly P(0):T₀={} is contained in every minimal spanning tree for G
+   - Induction Step:
+     - suppose P(k):Tₖ is contained in a minimal spanning tree T′ for G.
+     - By definition {t₁, t₂, …, tₖ} ⊆ T′ . If tₖ₊₁ also belongs to T′ ,then Tₖ₊₁ ⊆ T′ and we have P(k+1) is true.
+     - If tₖ₊₁ does not belongs to T′ ,then T′ ∪ {tₖ₊₁} must contain a cycle.
+     - This cycle would be for some edges s₁, s₂, …, sₖ in T′
+     - The edges of this cycle cannot all be from Tₖ or Tₖ₊₁ would contain this cycle.

![](bbox=[0.02, 0.52, 0.22, 0.78])