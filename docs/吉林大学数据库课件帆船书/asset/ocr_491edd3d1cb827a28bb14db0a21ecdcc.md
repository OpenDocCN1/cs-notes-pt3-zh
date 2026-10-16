# Join Strategies that Exploit Parallelism

+   - Consider r₁ ⋈ r₂ ⋈ r₃ ⋈ r₄ where relation rᵢ is stored at site Sᵢ. The result must be presented at site S₁.

+   - r₁ is shipped to S₂ and r₁ ⋈ r₂ is computed at S₂: simultaneously r₃ is shipped to S₄ and r₃ ⋈ r₄ is computed at S₄

+   - S₂ ships tuples of (r₁ ⋈ r₂) to S₁ as they produced;
+   S₄ ships tuples of (r₃ ⋈ r₄) to S₁

+   - Once tuples of (r₁⋈ r₂) and (r₃⋈ r₄) arrive at S₁ (r₁⋈ r₂)⋈ (r₃ ⋈ r₄) is computed in parallel with the computation of (r₁ ⋈ r₂) at S₂ and the computation of (r₃ ⋈ r₄) at S₄.

![](bbox=[0.0, 0.0, 0.095, 0.15])