# {0, 1, □, ▷} vs. Larger Alphabets

Suppose M has k tapes with the alphabet Γ.

A symbol of M is encoded by a string σ ∈ {0, 1}* of length log |Γ|.

States: A state q is turned into states q, ⟨q, σ₁¹, …, σ₁ᵏ⟩ where |σ₁¹| = … = |σ₁ᵏ| = 1, …, ⟨q, σ_{log|Γ|}¹, …, σ_{log|Γ|}ᵏ⟩ where |σ_{log|Γ|}¹| = … = |σ_{log|Γ|}ᵏ| = log |Γ|.

A computation step of M is simulated in M̃ by log |Γ| steps to read, log |Γ| steps to write, and log |Γ| steps to relocate the heads.