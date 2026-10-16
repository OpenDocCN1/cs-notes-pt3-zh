# Query Transformation

+   - Translating algebraic queries on fragments.

+   - It must be possible to construct relation r from its fragments

+   - Replace relation r by the expression to construct relation r from its fragments

Consider the horizontal fragmentation of the account relation into

```
account₁ = σ branch_name = "Hillside" (account)
```

```
account₂ = σ branch_name = "Valleyview" (account)
```

The query σ branch_name = "Hillside" (account) becomes

```
σ branch_name = "Hillside" (account₁ ∪ account₂)
```

which is optimized into

```
σ branch_name = "Hillside" (account₁) ∪ σ branch_name = "Hillside" (account₂)
```