# Effective Denumerable Set

Fact. ℕ⁺ × ℕ⁺ × ℕ⁺ is effectively denumerable.

Proof. A bijection ζ : ℕ⁺ × ℕ⁺ × ℕ⁺ → ℕ is defined by

```
ζ(m,n,q) ≜ π(π(m−1,n−1),q−1),
```

```
ζ⁻¹(l) ≜ (π₁(π₁(l))+1, π₂(π₁(l))+1, π₂(l)+1).
```